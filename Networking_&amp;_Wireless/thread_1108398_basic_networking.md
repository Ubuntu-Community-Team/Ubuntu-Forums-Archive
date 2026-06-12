---
title: "basic networking"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by Qbazic on 2009-03-27
Hi'i'm trying to get suse 6.2 running out on the net. I'm running it on a 300P2 with 256 ram. I run lspci and it lists my 3com card and ifconfig shows that lo and etho are up and running but i cannot ping any sites and when i do i get error message unknown host. I'm not sure how to edit a file which might need to be edited or what to change if i could. Any help would be appreciated thanks

---

### Post by Qbazic on 2009-03-27
Hi'i'm trying to get suse 6.2 running out on the net. I'm running it on a 300P2 with 256 ram. I run lspci and it lists my 3com card and ifconfig shows that lo and etho are up and running but i cannot ping any sites and when i do i get error message unknown host. I'm not sure how to edit a file which might need to be edited or what to change if i could. Any help would be appreciated thanks

---

### Post by Iowan on 2009-03-27
Suse is one version I've never used (which tempts the question: "Why ask here"), but it sounds like DNS issue.  Are you pinging by hostname or IP address?

---

### Post by Qbazic on 2009-03-27
I also ran dhclient and it states No DHCPOFFERS received and No Working leases in persistent database---sleeping

---

### Post by Qbazic on 2009-03-27
When i ping any website i get the error unknown host

---

### Post by davec64 on 2009-03-27
What happens when you traceroute?

Are you pinging the IP address or the FQDN?

Are you still getting to the site in a web browser?

If you're pinging a PC on a network is the ping response turned on?

On my Router I have Pinged turned off therefore you wouldn't get a response if you pinged me.

---

### Post by davec64 on 2009-03-27
Just tried Pinging ebay in Network tools and funnily enough I've got no response!

---

### Post by albinootje on 2009-03-27
> **Qbazic said:**
> Hi'i'm trying to get suse 6.2 running out on the net. I'm running it on a 300P2 with 256 ram. I run lspci and it lists my 3com card and ifconfig shows that lo and etho are up and running but i cannot ping any sites and when i do i get error message unknown host. I'm not sure how to edit a file which might need to be edited or what to change if i could. Any help would be appreciated thanks

SuSE 6.2 is really old. 
Please use Xubuntu 8.04.x on your old machine, or test first with Puppy Linux or another light-weight Linux distribution.

---

### Post by ktrnka on 2009-03-27
I just got Knoppix 6 running on the exact same specs on an IBM Thinkpad (old 300P2 256Mb ram 4GB HDD + wireless card). Try it! works great!

[http://www.knopper.net/knoppix-mirrors/index-en.html]("http://www.knopper.net/knoppix-mirrors/index-en.html")

---

### Post by Qbazic on 2009-03-27
I'm a new ubuntu user and need some help. Please post and point me in a direction to resolve problem. Please thank you

---

### Post by comradejanus on 2009-03-27
Whats the problem?

---

### Post by geezerone on 2009-03-27
Go to YaST ->Network Devices -> Network Card, select your card in the bottom of the screen, click on Change, then click on Edit. All the relevant settings are there. Try adding DNS settings first of all to get a dynamic IP assigned.

---

### Post by Therion on 2009-03-27
> **Qbazic said:**
> I'm a new ubuntu user and need some help. Please post and point me in a direction to resolve problem. Please thank you
No one can help you if you don't tell us, at a bare minimum what the problem is, what you've done to try and fix it yourself, what version of Ubuntu you're using and how you're using it -- installed to your hard drive, virtual machine, Wubi install.

---

### Post by Qbazic on 2009-03-27
i'll try to figure it out. I just wish i knew what direction to go

---

### Post by doas777 on 2009-03-27
> **Qbazic said:**
> i'll try to figure it out. I just wish i knew what direction to go

if you can fully describe the problem, we might be able to help. mabey not, but it's worth a try, right?

---

### Post by scottuss on 2009-03-27
Re-post with details of your problem and people may be willing to help. Posting meaningless gibberish will get you no help :mad:

---

### Post by boof1988 on 2009-03-27
I think the OP is talking about one of their other threads.  *dunno*

See [this thread](http://ubuntuforums.org/showthread.php?t=1108459).

---

### Post by doas777 on 2009-03-27
> **Qbazic said:**
> When i ping any website i get the error unknown host

whats the output of :
```

ifconfig
cat /etc/resolv.conf
nslookup www.google.com

```

---

### Post by Qbazic on 2009-03-27
> **doas777 said:**
> whats the output of :
```

ifconfig
cat /etc/resolv.conf
nslookup www.google.com

```

I'm bonkers but you have helped thanx Q

---

### Post by Qbazic on 2009-03-27
suse 6.2 has netscape 4.61

---

### Post by chili555 on 2009-03-27
He didn't answer any request for information in the other thread, so I don't think he really wants help.

---

### Post by Qbazic on 2009-03-27
thanks but 
i'm not sure how to figure out what your telling me. I want to learn e forum ebut the forum is hard.. to navigate the forum and i need help

---

### Post by chili555 on 2009-03-27
Please go back to the original thread here: [http://ubuntuforums.org/showthread.php?t=1108459](http://ubuntuforums.org/showthread.php?t=1108459)

See my post there.

---

### Post by boof1988 on 2009-03-27
> **chili555 said:**
> He didn't answer any request for information in the other thread, so I don't think he really wants help.

I think the OP is just having difficulties navigating the forums.  So it might be kind of us to have a little bit of patience and understanding in this case.

See this [thread](http://ubuntuforums.org/showthread.php?p=6969826#post6969826).

---

### Post by chili555 on 2009-03-27
Q-

First, bookmark this thread so you can refer back to it evry hour or so, whenever you like, to see what people have said to try to help you.

Next, go to Applications -> Accessories -> Terminal and type in:```
ifconfig
```Press enter. A bit of text will appear and please write it down and post it here so we can have the information we need to diagnose your problem. Do the same for:```
cat /etc/resolv.conf

```and for:```
nslookup www.google.com
```When posters say, 'What's the output of...' or 'Post the result of..." they usually mean a command at the terminal.

---

### Post by rhb on 2009-03-28
First of all, if you're running Suse you should post on a Suse forum, since there are some differences in the way things work.  I suggest you look at system log messages.  On Ubuntu I find that DMESG  and message logs sometimes report errors on my network card.  If you use a router, try talking to it first.  The ifconfig command can be helpful on most Linux systems.  The command "man ifconfig" will advise you how to use it, and trying to connect may show error messages either on the terminal or in system logs.

---

### Post by superprash2003 on 2009-03-28
in your terminal type **ping 74.125.45.100** .. whats the output?

---

### Post by superprash2003 on 2009-03-28
post output of **ifconfig** frm the terminal. what is your router's ip address?

---

### Post by bapoumba on 2009-03-28
Please go to the above quoted thread. Closing here.

---

### Post by ugm6hr on 2009-03-28
Mod comment:

I have merged about 10 threads, which are all related to the same issue.

Hopefully, some of the intended continuity will now make sense.

---

### Post by earthfarmer2030 on 2009-03-28
I'm new to Ubuntu (just got 8.04) don't even know if I'm in a right place for this post, I've been reading post regarding networkings and stuffs but can't seem to find 1 appropriate for my system ("I guess"). I just want to enable an FTP on my hardy, use remote desktop and try to share file on a windows computer.

Thanks very much in advance!!!! 

:confused:

---

### Post by doas777 on 2009-03-28
> **earthfarmer2030 said:**
> I'm new to Ubuntu (just got 8.04) don't even know if I'm in a right place for this post, I've been reading post regarding networkings and stuffs but can't seem to find 1 appropriate for my system ("I guess"). I just want to enable an FTP on my hardy, use remote desktop and try to share file on a windows computer.

Thanks very much in advance!!!! 

:confused:

thats a lot of ground to cover, so I'll give you some specific topics to research to get everything you want.

1) file sharing: you need to install samba. here is a good starting place for samba [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

2) Remote Desktop:
this is already built into it, but it is based on VNC.
you can configure teh server from System -> Preferences -> Remote Desktop
on the client, you will need to install and connect to the server with vncviewer

3) FTP: [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)
ask yourself if you actually need ftp. it's not all that useful unless you are actually providing downloads to the outside world.

good luck

---

