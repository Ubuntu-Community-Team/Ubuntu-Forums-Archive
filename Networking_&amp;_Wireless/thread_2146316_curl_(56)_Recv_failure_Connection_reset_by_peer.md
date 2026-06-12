---
title: "curl: (56) Recv failure: Connection reset by peer"
date: 2013-05-18
forum: Networking &amp; Wireless
---

### Post by anieruddha on 2013-05-18
[FONT=georgia][SIZE=3][FONT=microsoft sans serif]Hi,

We rented two ubuntu 12.04 machines on ec2 say box1 and box2.  On box1, we installed tomcat 7 and box2 we setup jenkins. Every hour we build 2 different war files on box2 & deployed to box1. Each war file is around 35-40 MB.  We use following command to deploy war files on tomcat.[/FONT][/SIZE]

 ```
[COLOR=#000000]curl [/COLOR][http://username:password@box1:8080/manager/text/undeploy?path=/]("http://jenkins:luckylue@ec2-50-112-58-251.us-west-2.compute.amazonaws.com:8080/manager/text/undeploy?path=/")

```[/FONT]```

[FONT=georgia] curl --upload-file application.war [http://]("http://jenkins:luckylue@ec2-50-112-58-251.us-west-2.compute.amazonaws.com:8080/manager/text/deploy?path=/&update=true")[username:password@box1]("http://jenkins:luckylue@ec2-50-112-58-251.us-west-2.compute.amazonaws.com:8080/manager/text/undeploy?path=/"):8080/manager/text/deploy?path=/&update=true[/FONT]
```
[FONT=georgia][SIZE=3][FONT=microsoft sans serif]
Deployment went fine for first time, but from second time onwards curl take too much time & return following error 

```
curl: (56) Recv failure: Connection reset by peer
```

I also check that command directly from console to check whether it something to do with jenkins. But from console also I am getting same error.

Can somebody please give some solution / workaround.

OS : ubuntu 12.04 server on both machines

Thanks.[/FONT][/SIZE][/FONT]

---

### Post by anieruddha on 2013-05-18
looks like bug exist on ubuntu only. I scrap both ec2 machines & create 2 other ec2 machine with rhel & did same installation/configuration. It working good uptil now

---

### Post by anieruddha on 2013-05-19
Its nothing to do with ubuntu, its firewall. Disabling firewall did the trick. Can somebody please tell me how I can add rule to ufw, so it can allow all request from particular address.

---

