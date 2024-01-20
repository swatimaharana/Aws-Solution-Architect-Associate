# IAM

    IAM = Identity and Access Management , Global Service
    * Users are people within the organization and can be grouped
    * Groups only contain Users and not other groups.

# IAM Permission 
Users and Groups can be assigned JSON documenets called policies. 


![Alt text](<Images/IAM Access.png>)



# IAM Policy Structure

Consists of :
```python
{
"Version" : "2012-10-17",
"Id" : "S3-Account-Permissions",
"Statement": [

        {
            "Sid" : "1",
            "Effect" : "Allow",
            "Principal" : {
                "AWS" : ["arn:......"]
                        },
            "Action":[
                "s3.GetObject",
                "s3.PutObject"
            ],

            "Resource":["s3/glue/emr"]

        }
]
}

```

    
    
    How a User can be given access to different AWS Resources? 

1. A User can be linked to a group and group is linked to an IAM Policy as a result the user inherits the access from the IAM Policy through the group.

2. A User can be linked with Inline Policies even if they are not associated to groups.

3. A User can be linked to different Groups which has different IAM Policies.

```python
{
"Version" : "2012-10-17",
"Statement": [

        {
            "Effect" : "Allow",
            "Action":"*",
            "Resource":"*"
        }
]
}

```

4. The IAM Policy is for admit access , Action can be modifies as per the level of access for the policy.

# IAM - MFA (Multi Factor Authentication)
In order to protect your root account and IAM user 

1. Use Strong Password
2. MFA = Password you know + Security device you own
3. Type of MFA Device 

    * Authenticator App -  Google Authenticator (Phone Only) , Authy (Multi Device)
    
    * Security Key ( Universal 2nd Factor (U2F)) - YubiKey By Yubico (3rd Party )

    * Hardware TOTP token - Hardware Key Fob MFA Device , Gemalto 


How a User can access AWS ?

* AWS Management Console  ( Password + MFA )
* AWS Command Line Interface (Protected by Access key) - Manage AWS Services through CLI .
* AWS SDK - Protected by Access Key - Manage AWS Services through Programming .
    * Language Specific APIs and embedded with application.
    * Access Keys can be created from the console.
    * Example - AWS CLI is built on AWS SDK for python : Boto   


# AWS CLI 

* Access key and Secret Key can be configured from the AWS Console and same will be required for logging in to AWS CLI.

* CLI and Console permisions are same and same operations can be perfeormed in both. 


# AWS CloudShell
*  A terminal in the cloud of AWS. 
*  Only Available in some region.


# IAM Roles 
* Selected a truested entity / Service 
* Add permission by attaching the role to a policy .
* Add Tags (Optional) and Provide a name to the role. 


# IAM Security Tool 
* IAM Credential Report (account - level)
    * Lists all your account's users and the status of their various credentials 
* IAM Access Advisor (user- level )
    * Sevice permissions granted to the user and when they are last accessed. 


# Best Practices :
* One Physical User = 1 AWS User ( Dont Share Credentials )
* Enforce MFA .
* Strong Password Policy 
* Dont Use Root Account except for AWS Account Set Up.
* Never share IAM user and Access Keys.
* Use ROLES for giving permission.
* Assign Users --> Groups & Permission --> Groups


