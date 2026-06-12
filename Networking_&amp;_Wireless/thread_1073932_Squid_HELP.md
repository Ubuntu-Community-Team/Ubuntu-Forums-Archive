---
title: "Squid HELP"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by mdsypr on 2009-02-18
I need help, I am not a novice and I have APACHE, GNUMP, WEBDAV all running on my server which took me awhile to figure out but I did it.  I also have SSH running and I can remote into my machine securely to surf the net which is great.

I now want to add in a proxy server, make it give a fake IP address so when I travel I can tunnel SSH into my server and use my proxy to surf without someone tracking everything I am doing.

I did the basic APT command, installed Squid 2.6 and I am using Webmin to tweak the settings.

My network is all based on 192.168.1.x .... I have tried everything and it keeps refusing connections and I am about ready to throw my computer out the window.  Why is SQUID so hard to figure out?

Can anyone, provide a simple step by step for someone and the key points on what to change and or look for to get it working.

This should not be this confusing, the cache, the ACL, the ports, etc.  This is why Ubuntu is not mainstream because I am considered a computer genius yet I can't even install Squid.

Plus, I can't even figure out how to attach my conf file here, I can't upload it is not a valid format and if I copy into word or txt the file size is too big.

Why does everything have to be a problem.  

I have searched all over this forum and Google for many, many hours and there is nothing that is step by step and easy enought to understand.

Someone please help.

Thanks,
Mike

---

### Post by mdsypr on 2009-02-20
It has been over a day and no one has posted a reply to my request for help.

I thought this was a place where people could go to ask for help?

Again, this is why Ubuntu is not mainstream and disappointing since it is a superior operating system.

Someone please respond and/or point me in the right direction.  I have read many threads, Google'd many articles and nothing is all encompassing and complete and no matter what I do I can not get my proxy server to work.

Thanks,
Mike

---

### Post by insineratehymn on 2009-02-20
> **mdsypr said:**
> It has been over a day and no one has posted a reply to my request for help.

I thought this was a place where people could go to ask for help?

Again, this is why Ubuntu is not mainstream and disappointing since it is a superior operating system.

Someone please respond and/or point me in the right direction.  I have read many threads, Google'd many articles and nothing is all encompassing and complete and no matter what I do I can not get my proxy server to work.

Thanks,
Mike

Being so aggressive won't get you far. I don't really understand what exactly doesn't work. You said you could SSH in, and the proxy was set up. But that it refuses connections? Elaborate further on the "refusing connections" part. Oh, and relax a little bit; most of us have day jobs and do this as a courtesy to others.

--edit--
I gotta go into the woods for a few hours. I'm not ignoring you, I promise.

---

### Post by mdsypr on 2009-02-20
Thanks for responding and sorry if you think I was aggressive, I wasn't seeing any response and given I have Apache setup, WebDav and Gnump music server this is really disappointing.

Yes I can SSH into my server and I can configure Firefox or any browser to use that connection via tunneling ... I now want to take it a step further and get a proxy server running so I can be anonymous.  

I have installed squid over 5 times, tweaked all the ACL settings and nothing seems to work.  I am sure it is a very simple thing but no matter what I do or what I tweak I can't get it to work.  I have Webmin which I use to adjust the settings, I put in the range of my IP's and made sure it was ALLOWED but again when I try to use the server it always refuses connections.

Like I said I have searched and searched and I can't find anything that is simple and complete that I can fully understand so I can get this to work.

I am sure it has something to do with a setting but again I know the server is running and I specified the IP addresses, etc.

I tried to attach the squid.conf file but it was an invalid format so not sure how else I can help.

Any good ideas?  Like I said I picked up Ubuntu with little help but squid is kicking my butt.

Thanks,
Mike

---

### Post by insineratehymn on 2009-02-20
Its cool.

Can I see your squid config file? If you have to, email it to me. Also, double check your router to make sure that it isn't the culprit. Sometimes those proxies run on a funny port or something. Make sure that box is essentially DMZd.

---

### Post by mdsypr on 2009-02-20
Ok I must be an idiot because I don't know how to email you.

Also, I have FIOS and actually the Verizon modem is easy to adjust and I have port forwarding on 3128 for my server.  Granted that is from the outside in, within my network I do NOT have a firewall running so I don't think that could be it but of course I am not sure.

If you can tell me how to get you the file I will send it along.

I think it has something to do with squid because the proxy is refusing connections so I think it is working, just blocking for some reason.

Thanks,
Mike

---

### Post by insineratehymn on 2009-02-20
Try this:

/usr/local/squid/etc/squid.conf

Try to post it on here if you can.

---

### Post by mdsypr on 2009-02-20
Ok, I compressed my squid.conf file from my server and attached it for you to review.

I can tell you the location you told me was not where I found it and not sure if that makes a difference or not.

I found it here: /etc/squid

Thanks
Mike

---

### Post by mpokrywka on 2009-02-21
I have two questions:

1. Your config has "cache_effective_user mike" and cache dir not configured (defaults are effective) - are you sure your user "mike" has permission to write to "/var/spool/squid" - default cache directory? (Is there any reason to change default cache_effective_user ?)

2. You have configured that only hosts with addresses 192.168.1.0/24 have permission to use proxy. Are you sure that when you use proxy your address is from this subnet?
I asked this, because you mentioned that you use ssh to connect, and when you use ssh forwarding your address on proxy will be different.
You can check /var/log/squid/access.log to see what ip addresses were denied access and you can reconfigure squid accordingly.

---

### Post by mdsypr on 2009-02-22
Thanks for the reply and I must say I am completely lost here so might make sense for me to use the original squid.confg and enter my IP addresses.  I am not even 100% sure how to do that and not even sure if I need to create a squid user to run it?  Also, I still want to be able to securely SSH into my server and then use the proxy to go out to the net.  I have SSH tunneling working fine, not sure how adding a proxy will work.

Therefore, if someone can guide me on the following basic questions I will reload the config file and try it out before I report.  I do have Webmin installed so I can configure it there or directly in the file, either way will work.

1) User name - I used my MIKE user name but I have read to use SQUID, I did check my system and I did NOT see a SQUID so I would have to create on?  I would have to make sure it is part of ADMIN so it can access the right files?

2) IP's - my home network has various computers on it, they are all in the 192.168.1.0 thru 192.168.1.200.  I did check and I am using 255.255.255.0 which is weird, usually I have seen 255.255.255.255.  How exactly do I enter this in the ACL part?  Also, do I HAVE to explicitly state to ALLOW this in the proxy restriction section?

3) Is there anything defaulted in squid that I need to remove in order to have it work?  I have read that my default squid will not work, you have to change something but I do not know what that is.

4) Anonymous - first is to get squid working but once I do it is another large task to make it anonymous for me to surf the net?

5) Cache - I use my computer ALOT and not sure if using the default cache will slow down my browsing or have no impact?  If so I do have 2 hard drives on my server and I can dedicate tens of gigs of space to a cache, if I need to some direction on how to do that would be great.

I do have port forwarding on my router for 3128 so if anything comes into my computer it goes to my server and Squid.

Any help is greatly appreciated.

Thanks again.
Mike

---

### Post by mpokrywka on 2009-02-22
I think your idea about "reloading config" would be best solution.

I have not used webmin, but I advise against its use, because I don't know what files webmin modify and how it interferes with default debian squid configuration - which is very sane btw.
You only need to edit (as root) /etc/squid/squid.conf - it is very well commented.

To make sure that your current config will not interfere with default installation I advise you to purge current squid install:
**sudo aptitude purge squid**
then make sure that /etc/squid/squid.conf does not exist (purge should delete it, but if it is not the case, delete /etc/squid directory)
Then:
1. Install squid:
**sudo aptitude install squid**
this should install squid and create proxy user
2. Edit default /etc/squid/squid.conf to configure:
 a) listening on internal network:
  **http_port 192.168.1.4:3128**
 b) add your internal network as allowed to access (insert this afrer line with remark "INSERT YOUR OWN RULE(S) HERE TO ALLOW ACCESS FROM YOUR CLIENTS"):
  **acl our_networks src 192.168.1.0/255.255.255.0**
  **http_access allow our_networks**

 Do not edit other lines now, defaults are good.
3. Reload squid to make sure config is in use:
**sudo /etc/init.t/squid reload**

Now try to use proxy with one of your hosts from home network.

About your questions:
1) no need to change defaults, don't bother
2) in point 3b above there is example of acl, there are two lines:
first: acl definition - means that "our_networks" will mean computers with source address 192.168.1.0 netmask 255.255.255.0
second: use "our_networks" acl to **allow** http access
3) no need to delete anything
4) "anonymous" means different things to different people, in case of proxy you can turn off X-Forwarded-For http header:
find and configure **forwarded_for off** in squid.conf (read comments)
or:
set **header_access X-Forwarded-For deny all** in squid.conf to disable proxy header completely
There is also "Via" http header that can be configured out similarly.
5) default squid cache setting is rather small:
"cache_dir ufs /var/spool/squid 100 16 256" - 100 means 100MB of cache
Change it to something bigger, but beware: bigger cache means more RAM used by squid (to index cache contents). Unfortunately I cannot advise you in this case.

---

### Post by mdsypr on 2009-02-25
Ok thanks for your help. So I did EXACTLY what you said I purged squid and yes I DID have to delete the /etc/squid directory.

I then re-installed and when it was installing I noticed something failed, said it didn't have a qualified visible host name or something like that.  So it kept loading and finally finished.

I went into squid.conf and make the 3 changes you suggested

http_port 192.168.1.4:3128

Un-commetted the next two lines and added the suffix
acl our_networks src 192.168.1.0/255.255.255.0
http_access allow our_networks

I then tried to reload like you said but it had nothing to reload so I just did sudo /etc/init.d/squid start

It said OK so I went into Firefox on my Vista machine and used the following for the proxy

192.168.1.4 port 3128.  I checked the box that said us this for all. I then tried to open a page.

NO LUCK

Still not working, refusing connections and I have no idea why and real, real annoying.  Like I said if all I had to change was 3 lines in the config file why is it not working?

I don't know anything about squid but I need to ask:

1) Does the following line mean it will listen to any IP that starts with 192.168.1.x?  Also, does /24 at the end do anything differently?

acl our_networks src 192.168.1.0/255.255.255.0

2) User name - I noticed nowhere did you made me change the confiq for a user name, does that mean anything?

3) Did anything happen due to that visible host name error when it was loading?

I need to get this working before I can mess with the cache size and change the header info.

I went into my Verizon FIOS router and confirmed that all IP addresses are 192.168.1.X and also confirmed that the subnet is 255.255.255.0 . 

Anyone have any ideas?  This is killing me.

Thanks,
Mike

---

### Post by mpokrywka on 2009-02-25
Answers:
1) 
```

http_port 192.168.1.4:3128

```
configures on which ip:port squid will listen

When squid is started run:
**sudo netstat -ltnp**
to see what **p**rocesses **l**isten on **t**cp ports (do **n**ot resolve dns), there should be line like this:
```
tcp        0      0 192.168.1.4:3128        0.0.0.0:*               LISTEN     28928/(squid)
```
If similar line is not present, squid is not listening or running at all.

Listening and access to proxy are two different things. Every host that can reach IP on which squid listenes may try to use proxy, but only those that have acl set, will be allowed.
You said: "I then tried to open a page. NO LUCK". Does that mean firefox displayed page with "Access denied, Access control configuration prevents your request from being allowed" or maybe something else?

2) "User name" - this part of configuration file you don't need to touch because when you install squid package, "cache_effective_user" is created automatically and you don't need to worry about that

3) "visible host name error" - this is probably root of your problems, I forgot about it because on my box I had hostname configured "correctly" and I needn't change this config setting.
Find line with: visible_hostname (probably below will be default: none) and add line:
**visible_hostname myproxy**
(any name should work)

Now restart squid: **sudo /etc/init.t/squid restart** and finally this should work.

Also after starting check bottom of /var/log/syslog for squid starting log, every errors should be visible there.

---

### Post by zeronothing on 2009-02-25
I myself is having trouble trying to understand this whole situation. what you want to do is from let say "the coffee shop" ssh tunnel into you machine at home. Then you want to then use the proxy running on the machine (at home) to hide your identify. then while your at the coffee shop type in the 192.168. whatever address (which is the address of the proxy machine) into firefox to configure it to use the proxy. From what I know ssh tunneling into your server at home doesn't necessarily make your pc at the coffee shop apart of the local network at home so you can reach the inside address 192.168 whatever. what I would do is just setup a simple VPN (hamachi), and connect through the VPN to make it seem like your apart of your local home network. Then you would be able to reach the inside address 192.168.(whatever) of your proxy server. I do this a lot with other services (not proxy particularity). I think the problem is with public address (which is the ip address seen on the internet) and the private address (which is seen internal on your home network 192.168 ). for an example I cant reach a windows machine running remote desktop from a coffee shop to my home using a 192.168 address. I have to use the Public address which is something like 66.176 etc. the beauty of VPN is it would make it seem like your at on your home network and then you would be able to access the private address 192.168. Just a thought man, I'm not trying to be mean or aggressive in anyway. I just thought this might spark an idea or a reason your having trouble with this whole situation.

---

### Post by mdsypr on 2009-02-25
Thanks I really appreciate your help so far with everything.  Well I still can't get it to work.

I did that netstat like you said and I couldn't find anything for my IP address.  When I tried to access it via Firefox I get the following error:

Proxy Server Refused Connection

The way I configured Firefox is to reference my server as

192.168.1.4 .... port to the right was 3128

I did NOT do anything with user name and I did go in and do:

visible_host myproxy

I then did sudo /etc/init.d/squid restart

Then tried netstat again, still can't find it and I am still getting refused connection in Firefox.

As you said I went into syslog to see errors and all I see in there are postfix errors, nothing related to squid.  I installed postfix via Webmin awhile back and never got it to work, I would like to completely get rid of it, how can I do that?

Any other ideas on squid?

Thanks,
Mike

---

### Post by zeronothing on 2009-02-25
Ok, first what I would do is setup squid and without ssh tunnel try to connect to the proxy to see if you can proxy out. you will need to be on your home network (I'm assuming two PC's) with your server and you client. try getting this part to work first before you try to access it outside your home network. if you can get that to work, then jump into the accessing it from the outside. if you want to know your public address just go to this [[COLOR="Blue"]webpage[/COLOR]]("http://www.whatismyip.com/") to see your Public address. now after you get it to work locally, then go some where like "the coffee shop" and try access your proxy using the public address. if you can get that to work getting the tunneling to work will take some elbow grease but at least you know your proxy is working. its been a while since I have messed with squid but I may try to set up a quick server at work tomorrow to do some testing.

---

### Post by mpokrywka on 2009-02-25
Ok, something is wrong...
Let's look at your config - paste output of:
**grep '^[^#]' /etc/squid/squid.conf**
(maybe sudo is required)

Also show us logs:
**grep squid /var/log/syslog**
Is there really nothing about squid?

---

### Post by mdsypr on 2009-02-25
Thanks everyone.

As requested attached is my squid.conf and my syslog zipped.

I agree about the SSH, until I can get this to work locally I won't worry about SSH for now.  

My server is 192.168.1.4 and my Vista machine is 192.168.1.3

I am always receiving the connection refused in firefox ... am I at least referencing the server correctly in it's settings?

Anything you guys can do would be greatly appreciated.

Thanks,
Mike

---

### Post by mpokrywka on 2009-02-26
In syslog there is a cause:
squid[8555]: /var/spool/squid/00: (13) Permission denied 
squid[8555]: ^IFailed to verify one of the swap directories, Check cache.log ^Ifor details.  Run 'squid -z' to create swap directories ^Iif needed, or if running Squid for the first time.

This is probably caused by previous installation with different "cache_effective_user" (by webmin), to resolve, delete cache directory:
**sudo rm -rf /var/spool/squid**
**sudo dpkg-reconfigure squid**
start squid:
**sudo /etc/init.d/squid start**

and check status in syslog:
**grep squid /var/log/syslog | tail -n 40**

Now squid should finally start...

BTW, this postfix install is really hosed, remove it altogether with broken configuration (aptitude purge postfix), but be sure to check what packages aptitude tries to remove with it - do not blindly say yes, there may be some other packages that requires MTA.

---

### Post by mdsypr on 2009-02-26
Holy crap, after almost of year it finally worked.  I can't thank you enough.

I still need to do what you said about the header info so I can surf anonymously and I will need instructions on how to make the cache very big, I do have 2 hard drives in my server and can probably dedicate 40 GB or more easily.

Then, I need to figure out how to SSH into it, I know how to SSH currently into my server with putty but to do that and then use the proxy will be interesting.

About the postfix issue, since it is totally fried can you tell me what NOT to delete if I do a purge?  Seems Webmin really screwed up that install as well, I think I learned my lesson with Webmin.

Thanks again.
Mike

---

### Post by mdsypr on 2009-02-26
And also need to figure out how to track where I go, I am sure there is a log or I think I heard for a tool to use with SQUID that gives you reporting?

SERG or something?

---

### Post by mpokrywka on 2009-02-26
About postfix:
invoke **aptitude --simulate --assume-yes purge postfix** (notice: no sudo here) and paste here result - we'll see if any additional packages are planned to be removed.

About squid logs:
check /var/log/squid/access.log, I don't use *sarg*, so I can't advise you in this case...

About cache size:
I think more than few GB (4?) is only waste of RAM (squid must use memory to index all cache).

About using ssh tunnel in Windows:
It is possible to do with putty, see attached image (in archive). Of course use this configuration after setting correct putty session options.
After putty connects, nothing more is displayed, you can configure firefox proxy as: localhost:8080.
To make it easier to use & change you should probably use some proxy switcher extension...
This putty window after login should remain open - as long as putty is active ssh tunnel is established

---

### Post by mdsypr on 2009-02-26
Thanks so much.  I will look at the putty files tomorrow afternoon.

I can tell you I did both of the following and when I went to WHAT IS MY IP it still found my IP so not sure how to correctly configure squid to be anonymous:

forwarded_for off 
header_access X-Forwarded-For deny all 

Can you also let me know how to configure squid.conf for the cache?

Once I have this running and it is completely anonymous I would love to have it setup so it runs automatically so when anyone jumps on my network they all go thru the proxy ... and to take it a step further I would love a login so I can really lock this down.

I do travel out of the county frequently and SSH and putty work great to connect to my computer in NJ and once squid is up I will be as secure and anonymous as I can be?

As requested here is what I received for that postfix error.

 aptitude --simulate --assume-yes purge postfix
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  hal-info libpq5 
The following packages have been kept back:
  gedit gedit-common sudo 
The following packages will be REMOVED:
  postfix{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 5 not upgraded.
Need to get 0B of archives. After unpacking 2695kB will be freed.
Would download/install/remove packages.


Thanks,
Mike

---

### Post by mpokrywka on 2009-02-26
You can remove postfix installation with broken config files (purge) freely, as that command that you tried said: you simulated purging postfix and "package manager" (aptitude) said that only one  package will be removed (postfix alone).

This anonymity question is complex, because you seem to think "anonymous" is different than my "anonymous". Every time you use your proxy, http requests leave through IP where your proxy is located (NYC?) and that IP cannot be changed. So only "anonymity" you'll get is that when you use your proxy when you are abroad (Europe for example), your "adversary" would see you as if you still posted from your home. If you wanted to be "really anonymous", you could use **tor** - but I have never installed it, so someone else must help you with that.

Other squid configuration questions are rather easy to solve when you really read this very well commented squid.conf file, you don't really need my help how to set for example cache size. I advise you to keep backup of good squid.conf configuration (now it works), and go with trial and error approach to manual configuration. After each file edit you reload squid (sudo /etc/init.d/squid reload) or restart if squid was not running and you check syslog for status: grep squid /var/log/syslog | tail -n 40
In syslog there will be messages about all configuration errors and important settings that are in place (cache size for example).

---

### Post by mdsypr on 2009-02-28
Thanks for all your help.  I have squid working for a few days now and even installed SARG and with Webmin I can see a ton of reporting of all the sites my machine has visited.  Let me tell you I don't want anyone else to see that ;-)

I was under the wrong assumption that using a proxy can make you anonymous while surfing.  I have poked around and edited squid.conf for the anonymous setting and some sites just don't work and I can still see my IP address when I visit whatismyipaddress.com.

Is there any easy and functional way to hide my IP address from the world or am I SOL?  I do have a few other computers lying around, can I make a few other proxy's and redirect?

I really have no idea so any ideas anyone has would be greatly appreciated.

I do still need to really figure out transparant proxy for all traffic, including https and then to add login requirements so I can be 100% sure my neighbors are not jumping on my network.

Thanks,
Mike

---

### Post by mdsypr on 2009-03-06
I want to thank all your help, again it is working but I still need to tweak the cache size and also figure out how to make it run transparent and with a login so I can really secure my network.

I was under the impression a proxy would make me invisible on the net, I realize now that the proxy needs an IP that is registered like the one I have with Verizon so I will never be invisible so that is a big disappointment to me.  

If anyone has any better ideas on how to surf and be invisible or as close to it I would love to hear your response.

Thanks,
Mike

---

