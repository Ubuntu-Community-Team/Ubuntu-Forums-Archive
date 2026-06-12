---
title: "DSL conection not working..."
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by DemoNMorph on 2009-10-31
Hello ! I just upgraded at Ubuntu 9.10 from Ubuntu 9.04,and my DSL conection does not working anymore...In Ubuntu 9.04 DSL conection worked,but now When I click on networks in the top of right screen appears my network hardware(Realtek and Atlansic from the MotherBoard) but it says : disconected both of them are disconected...I added a new DSL conection,i've entered my user and password but it's not working...In Windows 7 works great :(...Can anyone help me? :(

---

### Post by meho_r on 2009-10-31
It is a bug with Network Manager. There are couple of threads regarding this issue, you may want to search a little (e.g. [http://ubuntuforums.org/showthread.php?t=1303876&highlight=dsl+connection+karmic](http://ubuntuforums.org/showthread.php?t=1303876&highlight=dsl+connection+karmic) and bug report: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/438771](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/438771)). pppoeconf is seemed to be working fine. BTW, read the bug report, seems to be solved (maybe) using Network Manager from one of PPAs.

---

### Post by DemoNMorph on 2009-10-31
Ok thanks,but how did i configure my network because i'm newbie...,help me a little please.Thank You!

---

### Post by mourya on 2009-10-31
Im having the same problem.Eth 0 and eth 1 are recognized but when i try to auto connect they fail.The DSL doesnt connect without the ethernet device activated right?Being a newbie im stuck

---

### Post by meho_r on 2009-10-31
> **DemoNMorph said:**
> Ok thanks,but how did i configure my network because i'm newbie...,help me a little please.Thank You!

1. To update Network Manager using the one from PPA just open the Terminal (Applications > Accessories > Terminal) and run this command (just copy it and then right click in Terminal and Paste):
```
sudo add-apt-repository ppa:network-manager/trunk
```

2. After that type in Terminal this command:
```
sudo apt-get update
```

3. Next one is:
```
sudo apt-get upgrade
```

Summary: The first command adds PPA in your sources list, the second updates the sources list and the third one see if there's any updates and lists them waiting for you to confirm update process.

You may need to restart your computer after this. When it starts again, try connecting again (you did create a connection in DSL tab of Network Manager didn't you? It's a simple procedure: Right click on Network Manager > Edit Connections... > DSL > Add and input your username and password).

---

### Post by mourya on 2009-10-31
when i type sudo add-apt-repository ppa:network-manager/trunk

i get

<urlopen rror [Errno -2]  Name or service not known>

---

### Post by faical117 on 2009-10-31
Try with ->sudo pppoeconf

---

### Post by meho_r on 2009-10-31
> **faical117 said:**
> Try with ->sudo pppoeconf

Yes, try this in Terminal. I totally put aside that you actually DO NOT have Internet connection :oops: Just follow the instruction and when you get your connection working you may give a try what I said if you like to use Network Manager to start/stop connection in future (and not *sudo pon dsl-provider* command).

---

### Post by shaneon on 2009-11-02
Pl

---

### Post by DiogoFC on 2009-11-07
Here is what worked for me, but after trying a lot of solutions I don't which of them is responsible for that.

Probably it was forcing the following jaunty packages: network-manager, network-manager-gnome, libnm-glib0 and pptp-linux.

But only after two restarts [?] it did take effect, so maybe it was something else I did.

---

### Post by Maverick2011 on 2009-11-12
I have searched through many many threads, forums, the whole nine yards to connect my 9.10 ubuntu machine to a dsl modem. None of the methods seem to work. Any thoughts?

---

### Post by khaktus on 2009-11-18
The same issue for me on DSL. I was working on 9.04 for a few months without problem, now absolutely no internet connection on 9.10 - neither in Mozilla, nor in Synaptic. However, as I run dual boot with XP, on Windows, network connection is fine. Lucky me...

There are so many bugs launched and so many forums with dozens of workarounds for experts, creating new bugs... Can somebody write a step by step solution for newbie?

[COLOR=Red]0. The network is **not** working. (Don't tell me to download something).
1. What to do/rewrite/edit/launch to make a temporary workaround - network somehow working (mozilla, synaptic, or whatever)
2. What to do to download/get somehow some official fix (not creating new bugs) ... if it already exists.[/COLOR]

I'm not satisfied with answers like "upgrade NM with ppa" or "try pppoeconf"... it doesn't tell me much.
[B]
Please, someone, make a clear summary. [/B]

Do not send me another links to read endless forums... I have spent hours reading them... I'm used to the plurality of responses and solutions while working with Ubuntu, but having such a major problem, I'm loosing my patience. It is a major issue and newbies are not able to spend days reading forums, that offer so many workarounds, that need to be topped by other workarounds... I need to see what to do right now and not to read what hundreds of people tried... Where is Ubuntu's official solution? They should have a step by step fix on the first page of their web.

---

### Post by prat22 on 2009-11-21
I had the same problem, ie connection through network manager with a DSL connection. 

I came across this pppoeconf command, and got a temporary connection. Do the following:

0. Make your modem ready to dial, ie, make sure cables are connected, and link is ready.
1. Open terminal, and type su
2. Give root password
3. Type pppoeconf
4. Go through the instructions, and give required username/passwords.
5. You get connected! 

Once you are connected, you can see your network status by typing plog, and disconnect using poff -a.

Upto this, it should be fine, as it worked for me.


Then when you are connected, come back to this thread, and run those commands beautifully listed on the first page (adding repositories, update, upgrade, restart).
This has worked with many, but not me... I am still trying...;)

---

### Post by hoy on 2009-11-21
Hello. I don't want to add any PPA to my repository list, so... Is there any chance that this bug will be fixed someday with regular updates (I mean just 'apt-get update && apt-get upgrade' without adding PPA)? How long should I wait?

---

### Post by prat22 on 2009-11-21
The upgrade is currently in launchpad repository and is unavailable in normal upgrade...Till its given in the normal repository,it wont be available for upgrade

---

### Post by twin798 on 2009-11-22
I used the above instructions and had no luck.  A few websites will work with my DSL but most, like Google, will not. Gpodder will not download.  My Microsoft machine works fine to all websites.  9.10 is acting like when it was first released.  I did a fresh install back  then and DSL broke.  Now it is broken again.  I did the apt-get update and install.  Is 9.10 the Vista release of Ubuntu? :)

---

### Post by bob brazie on 2009-11-22
And when might this be?

If I know that answer I can plan on my 9.10 clean install.

And then I can stop lurking around this site and do some real work. <g>

Thanks, Bob.

---

### Post by dj.ricky on 2009-11-23
> **prat22 said:**
> I had the same problem, ie connection through network manager with a DSL connection. 

I came across this pppoeconf command, and got a temporary connection. Do the following:

0. Make your modem ready to dial, ie, make sure cables are connected, and link is ready.
1. Open terminal, and type su
2. Give root password
3. Type pppoeconf
4. Go through the instructions, and give required username/passwords.
5. You get connected! 

Once you are connected, you can see your network status by typing plog, and disconnect using poff -a.

Upto this, it should be fine, as it worked for me.


Then when you are connected, come back to this thread, and run those commands beautifully listed on the first page (adding repositories, update, upgrade, restart).
This has worked with many, but not me... I am still trying...;)

After trying the above, my DSL still won't connect and I now lost my eth0 !
I have no wired connections available now.

---

### Post by dj.ricky on 2009-11-23
> **faical117 said:**
> Try with ->sudo pppoeconf

After trying this I lost my eth0 wired connection.
DSL still wont work.
Only have wireless left.

---

### Post by AnandTerry on 2010-01-13
I have a dualboot with windows XP.
I have a WAN miniport connection which asks me for username and password. 

I am unable to make such a connection in UBUNTU 9.10

I get an active eth 0 connection in wired connections.
When i try sudo pppoeconf, it first shows me the active eth 0 connection and asks me if it is the only active connection. 
When i say yes i get some progress bars like 'scanning devices' , ' looking for pppoe access concentrator' , and then , i get a window saying 
'Sorry, I scanned 1 interface, but access concentrator did not respond. Please check your network modem cables. Another reason for the scan failure may also be another pppoe process which controls the modem'.

And in the teminal i get the following /user/sbin/pppoeconf:521:modconf:not found

I am tired of booting xp again and again in search of solutions. Could anybody please help?

---

