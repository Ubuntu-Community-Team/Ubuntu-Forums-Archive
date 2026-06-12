---
title: "Cant connect to Localhost trough lan!"
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by Nerflander on 2010-07-22
Ok i know it all sounds weard but ive been searching google so much now.... Cant seem to find the problem!

look the setup is kinda straight forward. We got a test server for websites. This server has lamp server configured. Now i have a Website in the apache www folder. From here on everything works fine in [http://localhost](http://localhost) or 127.0.1.1 etc etc. 

also i have configured virtualhosts. This so we can have a live enviroment but its actually a test enviroment.

Now i try to connect trough the lannetwork! so i goto my windows client and hit in the browser : [http://(serverip+port]("http://%28serverip+port")) and also tried [http://(serverip]("http://%28serverip")) 

When i do this i get a 403 forbiddin acces. I solved that problem by deleted a line in the apache2.conf wot was called : virtualHost xxx.xxx.xxx.xx: xx

Now Hes loading the page but says he cant connect to 127.0.1.1 

Any1 knows a solution? 

(sorry for my bad grammer btw :D)

---

### Post by Marctwo on 2010-07-22
'localhost' is normally 127.0.0.1.

This is from my '/etc/hosts' file:
```
127.0.0.1    localhost
127.0.1.1    ubuntu.ubuntu-domain    ubuntu
```I don't know why 127.0.1.1 hostnames are in there but I'm sure somebody somewhere has a use for them.

---

### Post by Nerflander on 2010-07-22
Hmh ye but the problem is in the begin of my apache install he automaticly used 127.0.1.1 so thats actually my localhost instead of 127.0.0.1


i checked it out and on 127.0.01 does the same thing. i quess its the same as 127.0.1.1

this is my host file

127.0.0.1          localhost
127.0.1.1          (servername)
192.168.19.24   (a domain name)
192.168.19.24   [www.(domainname).com](www.(domainname).com)
192.168.19.24   test.com   <--- this was just a test

i dont get wat i am doing wrong. ports are open etc. Router is not stopping it. etc etc virtualhosts are standing correctly.

---

### Post by Marctwo on 2010-07-22
It's probably beside the point anyway as I don't think the client should be trying to connect to either in the first place.

'localhost' refers to the client machine.  So, for example, 'http://localhost/about.htm' would work if you test from your server but a different client would look for that link on itself - but couldn't connect because it's not even running a server.

Any reference to localhost in the webpages should be replaced with you domain name and the domain name should be entered in the client machines hosts file with the ip address of your server.

I use this technique myself and it works for me.

---

### Post by Nerflander on 2010-07-22
i know. thats why its so strange caus it i would typ in:


[http://192.168.19.24](http://192.168.19.24)             it gooes to : 127.0.1.1/magento

then i get a 403 forbidden page.

I fixed that but now i get cant connect messege as if it doesnt exists but it says cant connect to :127.0.1.1 

but i dont know why it keeps refferring to the localhost.

---

### Post by Marctwo on 2010-07-22
How does it work if you use the domain name instead of the server ip?

---

### Post by Nerflander on 2010-07-22
i get the same page in my face. Unable to.... 

Since its a test server we didt lets the hosting company redirect it to our ip etc. So i changed my windows host file. In this way it should goto the server ip and do the job but not.

---

### Post by Marctwo on 2010-07-22
This is sounding more like an Apache config issue.  It's been a while since I had to look at mine but the basic idea that I use is:

Each site has it's own entry as a virtual host with a servername.  Any name that isn't configured as a virtual host will be handled by the default host.  So if you have 'site1', 'site2' and 'site3' all pointing to your server ip in your hosts files, they also need to be setup as virtual hosts in Apache on your server.

So if you type 'http://192.168.19.24/', it will be handled by the default host in Apache.  And if you type 'http://test.com' and you haven't configured a virtual host with the servername 'test.com' then that will also be handled by the default host.

---

### Post by Nerflander on 2010-07-22
jup and thats why i made virtual hosts for all of those things. 

for the test.com i made a test virtual host so i can check if without al the fancy database and php if it owuld load trough lan but also that host fails to load trough lan so thats why im getting desperate it aint working as it should be and im thinking of a clena install since for all the stuff i tried i did alot of tweaking in the configs. So im pretty dissapointed caus i mageged to creat a working magento install that was previous installed on a different server. And those magento installs are a PITA to move across servers.

i just dont get wots going wrong since i make virtual hosts for every test i role like test.com . 

Kind of weard but my next try will be a cleans erver install without gui and then install webadmin and all do it trough the webadmin gui...


lets hope that works.

---

### Post by Marctwo on 2010-07-22
I presume you've enabled name-based virtual hosting with the option:
```
NameVirtualHost *:80 
```
Other than that, I'm out of ideas.

---

### Post by Nerflander on 2010-07-22
Sorry to say. But yes i have!

thats why im getting desperate but im already doing reinstall from scratch.

anyway thx for help! i apreciate that you have helped

---

