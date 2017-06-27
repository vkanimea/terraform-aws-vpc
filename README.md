# terraform-aws-vpc

This repository contains a [Terraform][] project that builds [Scenario 2: VPC
with Public and Private Subnets][scenario_two] from the [AWS documentation][].
It's from [this blog post][blog_post] describing how it all works and is
designed to give a working example which can the basis of something much more
complex.

## Usage

`terraform.tfvars` holds variables which should be overriden with valid ones.

### Plan

```
terraform plan -var-file terraform.tfvars
```

### Apply

```
terraform apply -var-file terraform.tfvars
```

### Destroy

```
terraform destroy -var-file terraform.tfvars
```
## USE

amend terraform.tfvars with own AWS access, secret, keyname
amend public.tf  - amend with own availability_zone eg. in ap-southeast-2a, subnet_id
     resource "aws_instance" "web-1" {
       availability_zone = "ap-southeast-2a"      
       subnet_id = "${aws_subnet.ap-southeast-2a-public.id}"
amend private.tf - amend with own availability_zone eg. in ap-southeast-2a, subnet_id
      resource "aws_instance" "db-1" {
          availability_zone = "ap-southeast-2a"      
          subnet_id = "${aws_subnet.ap-southeast-2a-public.id}"        
amend variables.tf - amend with default aws_region, amis - image type eg. current ubuntu version
       variable "aws_region" {
          default = "ap-southeast-2"
       variable "amis" {
        ap-southeast-2 = "ami-47726224" # ubuntu 16.04 LTS
amend vpc.tf - amend as shown above

## Author

Copyright (c) 2015 Nick Charlton <nick@nickcharlton.net>. MIT Licensed.

[Terraform]: http://terraform.io
[scenario_two]: http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_Scenario2.html
[AWS documentation]: http://aws.amazon.com/documentation/
[blog_post]: https://nickcharlton.net/posts/terraform-aws-vpc.html
