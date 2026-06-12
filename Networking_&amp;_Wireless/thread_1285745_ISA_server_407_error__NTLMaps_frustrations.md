---
title: "ISA server 407 error / NTLMaps frustrations"
date: 2009-10-08
forum: Networking &amp; Wireless
---

### Post by B.A.L. on 2009-10-08
Hey all,

For a little project I have to get a Nagios environment running on my laptop in my employers network. I've got Ubuntu running in a virtual machine and firefox is running as it should, but I cannot for the life of me get apt-get and wget and such working. It's been 3 days now and I keep getting the same message:

''W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources)  407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy filter is denied.  )''

I've read that it is impossible to get Ubuntu itself trough the proxy and that you have to use a program called NTLMaps to translate the data for you so that you can get trough the ISa authentication. I have downloaded the .deb file, installed it, configured it, edited the proxy file in apt/apt.conf.d accordingly, and changed the proxy settings in Ubuntu itself to point to localhost port 5865 (that's where NTLMaps is listening on), but still I keep getting the same error. Another thing that is bothering me is that when I leave my password blank in the server.cfg file it should ask for the password when I try to make a connection but it doesnt, it justs puts out the 407 error once again, even tough the NTLMaps has started. Does anyone have any idea about what I'm doing wrong here? Thanks!

---

### Post by moebuspcgold on 2009-10-10
I had the same problem and tried NTLMaps but it was too slow for me.  So I used cntlm, however had similar problems with synaptic and wget at first.

What worked for me:
In System -> Preferences -> Network Proxy
Select manual proxy configuration, Same proxy for all protocols
http proxy = 127.0.0.1
port = 5865 (in your case)
In details make sure that 'Use Authentication' is not ticked.
Then apply it System wide.

System -> Administration -> Synaptic Package Manager
In Synaptic Package Manager go Settings -> Preferences then Network
http and ftp proxy = 127.0.0.1
port = 5865
Click authentication and make sure this is blank.

In your NTLMaps config file make sure that everything is entered including the windows domain name.  The windows network domain is used in the authentication.
Since I used cntlm, I made sure that the Username Password, Domain, Proxy and Listen were entered in the file /etc/cntlm.conf

Restart the PC (For simplicity sake this is important)

Check if the proxy setting have been updated properly.
Open a shell and type:
```
export | grep proxy
```You should see something exactly like this:
```
declare -x ftp_proxy="ftp://127.0.0.1:5865/"
declare -x http_proxy="http://127.0.0.1:5865/"
declare -x https_proxy="https://127.0.0.1:5865/"
```also check your etc/apt/apt.conf file to see if the proxyies have been changed to 127.0.0.1:5865

Now test to see if wget works from a command line
```
wget www.google.com
```It should display that it is checking 127.0.0.1:5865, and download the correct file.
If it fails then something is wrong with NTLMaps setup.

Your Synaptic Package manager should be working correclty now as well.

I recommend cntlm over NTLMaps for several reasons.

[LIST=1]
[*]It is heaps faster then NTLMaps (in my experience).
[*]It allows hashing of your proxy password so it is not cleartext in the config file.
[*]It allows multiple proxies to be entered, so if one falls over it will jump to the next and jump back if necessary.
[*]You can set it to deny requests from anything but localhost so the whole LAN will not see your local proxy port open.
[/LIST]
Hope this helps.

---

### Post by B.A.L. on 2009-10-12
Thanks for the reply, but in the mean time I have already found out about CNTLM, and I got it working! It still needed a lot of tweaking (I had to struggle with password hashes and the choice between NT, LM, NTLM or NTLMv2 authentication), but I finally got it working...you have no idea how relieved I was to finally get a simple apt-get update command working behind that evil ISA proxy. :p

Anyway, for people reading this topic to look for help because they cant get trough the ISA proxy (it's hell, isn't it?), here the information I used to get trough:

[http://cntlm.sourceforge.net/](http://cntlm.sourceforge.net/)
The main site with download links, and pay special attention to the ''configuration hints'' section on the main page, some useful information there

[http://iitmlug.a.wiki-site.com/index.php/Cntlm](http://iitmlug.a.wiki-site.com/index.php/Cntlm)
[http://www.cse.iitm.ac.in/~osslab/wiki/index.php?title=Cntlm](http://www.cse.iitm.ac.in/~osslab/wiki/index.php?title=Cntlm)
These both contain the same info so when one is down try the other. An informational wiki, especially when it comes to the installing proces.

[http://www.leg.uct.ac.za/howtos/use-isa-proxies](http://www.leg.uct.ac.za/howtos/use-isa-proxies)
Written for people with similar problems, and some useful tips...pay special attention to the password hashes, the authentication type and the export http proxy command (!!!), those did the job for me.

To anywone ever reading this; good luck! :P

---

### Post by Freebies on 2010-08-23
[FONT=Verdana][COLOR=Navy]Great stuff...worked like a charm![/COLOR][/FONT]
:popcorn:

---

### Post by timur_ba on 2011-05-06
The same problem is also here: 
[http://ubuntuforums.org/showthread.php?t=1020784](http://ubuntuforums.org/showthread.php?t=1020784)
[http://ubuntuforums.org/showthread.php?t=964746](http://ubuntuforums.org/showthread.php?t=964746)
[http://ubuntuforums.org/showthread.php?t=1285745](http://ubuntuforums.org/showthread.php?t=1285745)
[http://ubuntuforums.org/showthread.php?t=1396749](http://ubuntuforums.org/showthread.php?t=1396749)
[http://ubuntuforums.org/showthread.php?p=10777002](http://ubuntuforums.org/showthread.php?p=10777002)

I opened a bug for this:
[https://bugs.launchpad.net/ubuntu/+bug/724849](https://bugs.launchpad.net/ubuntu/+bug/724849)

---

### Post by Zayed on 2011-08-27
Awesome But Still No luck for Yahoo IM Connecting .. if nyone Get Succeeded Let Us Know :p

---

