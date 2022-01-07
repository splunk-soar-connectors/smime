[comment]: # "Auto-generated SOAR connector documentation"
# S/MIME

Publisher: Splunk Community  
Connector Version: 1\.0\.3  
Product Vendor: S/Mime  
Product Name: S/MIME  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 4\.8\.24304  

This app provides support to S/MIME integrations

[comment]: # " File: readme.md"
[comment]: # "  Copyright (c) 2020 Splunk Inc."
[comment]: # ""
[comment]: # "  Licensed under Apache 2.0 (https://www.apache.org/licenses/LICENSE-2.0.txt)"
[comment]: # ""
## Licensing details for the app

### M2Crypto

This app uses the M2Crypto module, which is licensed under the MIT License (MIT), Copyright (c) Ng
Pheng Siong.

### typing

This app uses the typing module, which is licensed under the Python Software Foundation License
(PSF), Copyright (c) Guido van Rossum, Jukka Lehtosalo, Lukasz Langa, Ivan Levkivskyi.

## <span id="Requirements_2"></span> Requirements

Supported OS is CentOS 7+

Access your Phantom instance via Terminal and install following OS dependencies

            
            # Install library and its dependencies
            $~ sudo yum install python-devel openssl-devel gcc gcc-c++
            
          

## <span id="Keys_and_Certificates_3"></span> Keys and Certificates

To use this app you need to provide an RSA key pair (this consists of a public key and a private
key) and an X.509 certificate of said public key.

To generate a new RSA key pair, you could install and use OpenSSL on a CentOS 7 instance. Once
properly installed, execute the following commands to create key pairs and certificates.

            
            # Create a pair of keys
            $~ openssl req -newkey rsa:1024 -nodes -x509 -days 365 -out cert.pem

            # Rename the private key
            $~ mv privkey.pem key.pem
            
          

The generated keys and certificates will be used to configure a S/MIME Phantom asset.


### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a S/MIME asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**private\_key** |  required  | file | Private Key \.pem file
**public\_key** |  required  | file | Public Key \.pem file

### Supported Actions  
[sign email](#action-sign-email) - Sign email message body  
[encrypt email](#action-encrypt-email) - Encrypt email message body  
[decrypt email](#action-decrypt-email) - Decrypt email message body  
[verify email](#action-verify-email) - Verify signed email message body  

## action: 'sign email'
Sign email message body

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**message\_body** |  required  | The message body to send signed | string |  `smime email message body` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.message\_body | string |  `smime email message body` 
action\_result\.data\.\*\.SMIME\.message | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'encrypt email'
Encrypt email message body

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**message\_body** |  required  | The message body to encrypt | string |  `smime email message body` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.message\_body | string |  `smime email message body` 
action\_result\.data\.\*\.SMIME\.message | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'decrypt email'
Decrypt email message body

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**encrypted\_message** |  required  | The encrypted message body to decrypt | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.encrypted\_message | string | 
action\_result\.data\.\*\.SMIME\.message | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'verify email'
Verify signed email message body

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**signed\_message** |  required  | The signed message body to verify | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.signed\_message | string | 
action\_result\.data\.\*\.SMIME\.message | string | 
action\_result\.status | string | 
action\_result\.message | string | 
action\_result\.summary | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 