---
title: "Connect to server using hostapd and access web application by name"
date: 2011-09-21
forum: Networking &amp; Wireless
---

### Post by gunsnrails on 2011-09-21
Hi,

I posted the same thing in stackoverflow but I'm not sure that's the right place for this question. I'll close the one that gets solved first.

         I am building a box where I have a Rails application running.  I'm using Linux Ubuntu 11, Rails 3.0.5 and using Thin server for the  application.

  I am setting a USB wifi adapter in master mode so other devices can  connect to the box and access the Rails app. The adapter is using the ip  10.10.0.1 and it is working fine, devices can connect and so. I use  hostapd to handle the device connections.

  Now if I start thin on ip 10.10.0.1 and port 80 I can get to the rails application from the device using [http://10.10.0.1]("http://10.10.0.1/")

  But I would like to be able to access the application with a name like [http://myapp]("http://myapp/") I have tried adding 10.10.0.1  myapp to the /etc/hosts but it didn't work.
  How can I do that?

  I'm not sure this is the best way to do the connection between the  adapter and the Rails application, so any advices will be appreciated. Like is Thin alone acceptable, or should I put Nginx in front for  example. Should I run the app on another ip and use some iptables rule to do the  connection...etc

  Thanks!

---

