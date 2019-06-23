# AWS-SharingFilesBetweenMultipleEC2
Sharing files and Data between Multiple EC2 Instances based on EFS Service

EC2 instance communicating with the mount target via a TCP/IP network connection. EFS mount target making the data available to EC2 instances via the NFSv4.1 protocol in a single AZ. Security groups used to control which traffic is allowed to enter the mount target. The NFS protocol uses port 2041 for inbound communication.

The client security group is attached to all EC2 instances that want to mount the filesystem. The mount target security group allows inbound traffic on port 2041 only for traffic that comes from the client security group. This way, it makes possible to have a dynamic fleet of clients who are allowed to send traffic to the mount targets.

The mount target references the filesystem, linked to subnets, and also protected by the security groups.

