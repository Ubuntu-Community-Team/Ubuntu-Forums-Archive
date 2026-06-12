---
title: "ssh tunneling with non default (port 22) used for ssh?"
date: 2010-03-08
forum: Networking &amp; Wireless
---

### Post by extendedping on 2010-03-08
ok here is my somewhat convoluted situation. I installed this dd-wrt.com os on my linksys wireless g router and now I can do 2 neat things. ssh into my linksys and run /usr/sbin/wol -i x.x.x.255 my-home-machine-macaddress, and start my home machine from libraries starbucks/etc. because starbucks etc have most ports shut I have only found 2 I can depend on. port 80 and port 443. so I changed the default ssh port on the linksys from 22 to 80 enabling me to ssh into that using either ssh -p 80 root@x.x.x.x or (using no-ip dynamicdns) ssh -p 80 root
@my-unique-no-ip-name.zapto.org (root is the default dd-wrt name I don't know how to change it). So port 80 ssh is great and I can go into my always on little linksys from anywhere and start up my home pc. or now, as I said the only other always opened port seems to be 443. so on the linksys I forwarded that port to my home pc (192.168.1.10). on my ubuntu box (.10) I changed the default ssh port in the ssh config file from 22 to 443. so now from starbucks etc I can ssh directly into my home ubuntu box by going ssh -p 443 mylocalubuntuusername@mylinksysip or at ssh -p 443 [email]mylocalubuntuusername@my-unique-no-ip-name.zapto.org[/email]. 

so in a nutshell I setup 80 to let me ssh directly into my linksys (enabling me to turn on my local ubuntu or ssh into it from the router), and I set up 443 as port forwarded on the linkysys to the local ubuntu home box, which had its ssh config listen port changed from 22 to 443, enabling me to ssh directly into my home box from behind library/starbucks firewall. once ssh'd in I can fire up my virtual machines using virsh for learning purposed. so overall this is pretty neat. here is the issue. 

I am just learning linux and want to learn web design. as such I want to be able to use apache to learn the lamp stack on the ubuntu home pc. the issue is now my port 80 and my port 443 are gone for remote testing of anything I set up on the home ubuntu pc. port 80 takes me to ssh in my linksys and 443 gets me directly to ssh on the home ubuntu box. so lets say I set up a web site on the apache home ubuntu. I cannot display the page on my laptop sitting at starbucks because 80 at that address takes me to ssh on my router. I can't set up apache on 443 enabling me to test my website by typing in my brouser myname.zapto.org, cause i already changed the home ubuntu to 443 which is forwarded through the linksys. now..

I have read about ssh tunnelling and have tried varous commands to try to tunnel 80 on the home machine through a tunnel to my laptop at starbucks but I can't get it working. I don't know if this has to do with the fact that I am using ssh on a non default port or another issue like I just don't understand the command. anyway what i have tried is

ssh -L 8080:localhost:80 -p 443 me@my-linksys-ip-address -- and
ssh -L 8080:localhost:80 -p 443 me@my-linksys-ip-address -N

the former logs me into my home ubuntu after prompting for the password no issues. however from my browser putting in myname.zapto.org:8080 gives me page not found. the former prompts for my password and then hangs (I think it took and I should just be putting & at the end of the command, but results in the same page not found from the laptop browser.

from home if I put my local ip 192.168.1.10 into my laptop browser it takes me to the default apache "it works" on the ubuntu box so I know apache is running fine on port 80 on the home ubuntu. so basically....I don't have a clue how to access the local testing/learning-lamp site from a remote browser through a ssh tunnel. or if it is even possible given the strange configuration I have set up to access the router and the home ubuntu via ssh. anyway I know that was a major mouthful if you can follow it (I can't) and get me a solution, I will post your name on my default apache page in lights....thanks...

---

### Post by Skaperen on 2010-03-08
Try this on your browser:  [http://localhost:8080/](http://localhost:8080/)

---

### Post by extendedping on 2010-03-08
> **Skaperen said:**
> Try this on your browser:  [http://localhost:8080/](http://localhost:8080/)

bling it works. I am in my house so I will have to check it from outside but I am using the ssh command using the ip of the local ubuntu box and using the real ip 74.x.x.x of the linksys and the localhost:8888 works. I am going to have to draw a map of what is going on here, anyway thanks so much I never would have typed localhost, I would have kept putting the linksys address in my browser. 

how cool is this? using linux I can access my home pc from anywhere (well anywhere I have tried at least) and even turn it on remotely...

fu windows 7...

---

### Post by Skaperen on 2010-03-08
For it to work from "outside" you have to use a hostname or IP address that goes to the machine that is running the ssh client.  That machine knows itself as "localhost" because that's the standard for a machine to reference itself.  I still don't understand your network topology so I don't know if you are running ssh from where you need to do not.

---

### Post by extendedping on 2010-03-08
> **Skaperen said:**
> For it to work from "outside" you have to use a hostname or IP address that goes to the machine that is running the ssh client.  That machine knows itself as "localhost" because that's the standard for a machine to reference itself.  I still don't understand your network topology so I don't know if you are running ssh from where you need to do not.

the setup is this

home ubuntu pc on a 192.x network no dhcp connected to my linksys 
linksys has a 74.x.x.x which never seems to change on its outside interface but I setup dynamic dns on it anyway in case it does change 

the linksys has a new os on it a small linux that I can ssh to. the default port to ssh to on that has been changed to 80 (this is under the exteral access tab on the linksys, I can still connect to it locally 192.168.1.1 on port 22) so it will always be available to me (well I hope at least) and will let me start my directly attached 192.x.x.x ubuntu box using wake on lan. I can also ssh then from the linksys to the ubuntu box but I am just using the linksys to turn on the home pc so I also have the linksys forwarding 443 to my internal ubuntu 192.x.x.x. box. so if my computer at home is left on I never even need to ssh to the router on port 80 I can just ssh directly to the home box by typing ssh -p 443 me@my-dyn-dns-or-linksys-ip. 
now to tunnel to see my dinky (all it says so far is "it works") web site I do ssh -L 8888:localhost:80 -p me@my-dyndns-or-linksys-ip. I am now ssh'd into the local ubuntu box and from my laptop when I type in firefox url box localhost:8888 I see my home ubuntu apache welcome "it works".

what I was saying is that I have not actually left my house today so I have tried the  ssh -L 8888:localhost:80 -p me@my-dyndns-or-linksys-ip
which (to my limited understanding) means I am actually going out to the internet and then back in through the linksys. I have also tried
 ssh -L 8888:localhost:80 -p me@my-local-192.x.x.x-address and that worked as well. I am fairly sure this tunneling will work when I am physically outside trying it at a starbucks or library but I guess I will not know till I try it. but everything else I have tested from within my house by specifying the linksys real or 74.x.x.x address has worked just like I was sitting in a starbucks (for instance ssh to the internal side of my router at 192.168.1.1 works on port 22 but to ssh to the external 74.x.x.x even from within my house I have to put the port 80...anyway thanks much, its really cool that ssh trick and this wake on lan...

---

### Post by extendedping on 2010-03-10
ok but can I do this?

so now remotely I can access my default (home ubuntu compter) apache using 
ssh -L 8888:localhost:80 -p 443 me@my-ip -N

and then in my browser put... 
localhost:8888

but what if I want to see the page at 
localhost/drupal6

I have tried 
ssh -L 8888:localhost/drupal6:80 -p 443 me@my-ip -N

but this fails. so is there any way to ssh tunnel the non default apache site?

thanks got it....from the browser localhost:8888/drupal6

---

### Post by Skaperen on 2010-03-10
Let me see if I can understand this.

On the linksys router running an upgraded Linux (OpenWRT or whatever) you have it configured so:

1.  sshd listens on port 22 only on the internal 192.168.x.x interface
2.  sshd also listens on port 80 on either the external 74.x.x.x interface or both interfaces
3.  forwards connections to port 443 on to the ubuntu box port 443.

You want to do "ssh -L 8888:localhost:80 -p 443 me@my-dyndns-or-linksys-ip" or "ssh -L 8888:localhost:80 -p 443 me@74.x.x.x" and get in to your web server.  I think that should work like that.  You need to test it and see.

You want to test the setup by trying it from INSIDE your network.  That MAY work.  Can you ping the 74.x.x.x address from INSIDE your network (e.g. from your Ubuntu box)?  If you can, then this should work, but no guarantees (connecting to an interface going backwards doesn't always work right for reasons I've not fully understood).

However, your Drupal "trick" won't work.  OpenSSH wants only a hostname or IP address in the 2nd to last argument for the -L option.  The only way to access the "drupal6" directory on the web site is to specify that in the URL so it goes in as part of the HTTP request (that's how HTTP does it).

So once you get it so the URL [http://localhost:8888/](http://localhost:8888/) works, then try [http://localhost:8888/drupal6](http://localhost:8888/drupal6) and see what you get.

If you want to "magically" access the "drupal6" directory without specifying a directory in the URL, you have to change that on the web server on the Ubuntu box (I assume Apache, and that can be done via some aliasing directives), or else use a proxy server that can remap URIs like that (I believe Apache in proxy mode can do that).  If that is what you want to do, and don't want to change in the primary server itself, what is the scope of this change? Just from accessing via the ssh tunnel?  That won't happen from ssh itself.

FYI, I run a squid proxy server at home.  I have a rented dedicated server running Debian.  My home box runs a cron job that runs (approximately ... there's a lot more in it that that) "ssh -R localhost:3128:localhost:3128 -f -N me@myserver".  Then from somewhere else I "ssh -L localhost:3128:localhost:3128 -f -N me@myserver" and configure the browser to use "localhost:3128" as a proxy server.  It goes out the 2nd ssh to connect to port 3128 on my server (which only takes such connections from itself, not from the net) which then takes it into my home box which connects to the squid proxy there. I can then surf the net ... or my local LAN ... just as if I were at home ... but do it from anywhere I can safely initiate that 2nd ssh session.

---

### Post by extendedping on 2010-03-10
omg i'm lost with the squid and cron job.  yes you have my setup exactly and are correct in how to access the drupal dir. btw everything does work from outside (tried library, b&n, and sbucks).

---

### Post by Skaperen on 2010-03-11
Well, if everything works from outside, you should be good to go.  To get it to work from inside, if hitting the IP address of the interface facing outside does not work, then you will need to hit the other IP address of the other interface ... the one facing your LAN ... instead.  If you really want to make it work using exactly the same hostname, you'll need to apply some DNS tricks.

---

