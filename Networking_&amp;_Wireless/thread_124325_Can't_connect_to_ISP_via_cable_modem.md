---
title: "Can't connect to ISP via cable modem"
date: 2006-02-01
forum: Networking &amp; Wireless
---

### Post by Randux on 2006-02-01
I'm new to linux and I have downloaded a bunch of live distros and am trying them out.  I have not been able to connect to my ISP from any of them!

I have a two ethernet cards (wireless and regular) and a cable modem.  On Windows I have a definition for the ethernet card, and one for the connection to the ISP.  In the ISP connection object I specify the ip address of the ISP, my userid, password, and some protocol/connection specific stuff.

I cannot find (on any of these distros that I've looked at) how and where to enter information like the IP address of the ISP, my userid, password, etc.  My connection isn't DSL and it's not dial-up, and these are the only two kinds of connections that I seem to see mentioned with respect to any of the live distros I've tested.

I searched the boards here and the only thing I found which may be relevant is a mention that someone else had a problem because he also had two ethernet cards, one wireless, one regular, and he ran with his wireless card disabled.  Therefore ubuntu didn't recognize eth1.  I am not a linux/communications/pc guy so I am very lost.  I also run with my wireless card disabled, and I don't want to enable it.

Can someone please explain the all the steps necessary to define this connection, and any other information I'll need to connect to the internet?  Or if this is already discussed somewhere else, if you can give me a pointer that would be great.

Thanks!

Rand

---

### Post by mips on 2006-02-01
Ok, lets first get familair with your setup.

1. What Brand & Model cable modem do you use, web link please ?
2. Who is your ISP, web link please ?

For the next steps ensure your cable modem is on and connected to the PC (working or not)

3. From a Windows cmd/dos prompt type **ipconfig /all** and paste the entire output here.

4. From Ubuntu terminal type **ifconfig -a** and paste the entire output here.

5. From Ubuntu terminal type **route -n** and paste the entire output here.

---

### Post by Randux on 2006-02-01
Thanks very much for offering to help.  I can see that you have a systematic approach which is good.

I don't know how to get the output from ubuntu into a file I can read from Windows to post here- although earlier today I did capture the ipconfig output from Windows which I'll post here (note, I've asterisked all addresses and unique fields).  BTW, I captured the ipconfig ouput when I was connected to my ISP with everything running normally under Windows.

What about this, that I wrote earlier: "My connection isn't DSL and it's not dial-up, and these are the only two kinds of connections that I seem to see mentioned with respect to any of the live distros I've tested."  How and where do I specify the ISP ip address, my userid, and password?

Thanks very much.

Rand.



Windows IP Configuration



        Host Name . . . . . . . . . . . . : ********

        Primary Dns Suffix  . . . . . . . : 

        Node Type . . . . . . . . . . . . : Unknown

        IP Routing Enabled. . . . . . . . : No

        WINS Proxy Enabled. . . . . . . . : No



Ethernet adapter Local Area Connection:



        Connection-specific DNS Suffix  . : 

        Description . . . . . . . . . . . : Intel(R) PRO/100 VE Network Connection


        Physical Address. . . . . . . . . : **-**-**-**-**-**

        Dhcp Enabled. . . . . . . . . . . : Yes

        Autoconfiguration Enabled . . . . : Yes

        IP Address. . . . . . . . . . . . :  ***.**.***.***

        Subnet Mask . . . . . . . . . . . : ***.***.***.*

        Default Gateway . . . . . . . . . : ***.***.***.*

        DHCP Server . . . . . . . . . . . : ***.***.***.*

        DNS Servers . . . . . . . . . . . : ***.***.***.*

                                            ***.***.***.*

        Lease Obtained. . . . . . . . . . : February 1, 2006 hh:mm:ss xx

        Lease Expires . . . . . . . . . . : February *, 2006 hh:mm:ss xx


PPP adapter cable:



        Connection-specific DNS Suffix  . : 

        Description . . . . . . . . . . . : WAN (PPP/SLIP) Interface

        Physical Address. . . . . . . . . : **-**-**-**-**-**

        Dhcp Enabled. . . . . . . . . . . : No

        IP Address. . . . . . . . . . . . : ***.***.***.***

        Subnet Mask . . . . . . . . . . . : ***.***.***.***

        Default Gateway . . . . . . . . . : ***.***.***.***

        DNS Servers . . . . . . . . . . . : ***.***.***.***

                                            ***.***.***.***

        NetBIOS over Tcpip. . . . . . . . : Disabled

---

### Post by mips on 2006-02-01
[QUOTE=Randux]Thanks very much for offering to help.  I can see that you have a systematic approach which is good.

I don't know how to get the output from ubuntu into a file I can read from Windows to post here- although earlier today I did capture the ipconfig output from Windows which I'll post here (note, I've asterisked all addresses and unique fields).  BTW, I captured the ipconfig ouput when I was connected to my ISP with everything running normally under Windows.

What about this, that I wrote earlier: "My connection isn't DSL and it's not dial-up, and these are the only two kinds of connections that I seem to see mentioned with respect to any of the live distros I've tested."  How and where do I specify the ISP ip address, my userid, and password?

Thanks very much.

Rand.


Windows IP Configuration



        ********
[/QUOTE]

You can copy the output to a text editor like gedit or kate depending on whether you use gnome or KDE.

you can save this on a memory stick/stiffy or if your windows partition is FAT32 (not NTFS) mount it and save the data there to be used from windows.

*** out all the info does is just as good as not providing me with the info. If you feel your info is unsafe then you can PM me or E-mail me with it. I will not distribute it and will delete it once your problem is sorted out.

The process is going to basically be a question and answer session where I will ask some questions and you will probably respond with information. If you cant supply me with the info then I cant do much.

If you prefer you can PM or Email me and we can communicate that way outside of a public forum. Have done this before and it is not a hassle. I will even initiate it in some instances if I believe the info is very sensitive and not for public scrutiny, vpn setup etc.

I'm off to bed now so if you reply, pm, email me and i dont respond you know why, i'll be back in the morning ;)

---

### Post by Randux on 2006-02-01
Hi, I didn't expect that you would also be up ;-)  We're in the same time zone.

Sorry, I didn't realize that those addresses were critical.  But maybe we can look at things from another angle:

I can see the home page of my backbone provider from the web browser.  This is exactly what happens if I open a browser in Windows but haven't "dialed" my ISP.  So I don't think the problem is hardware- it's simply understanding how to set up the "dialer" for cable.  The connection to the cable provider is working, from my pc, through the cable modem.  The question now is how I tell my cable provider to gateway me to my ISP.

Maybe all of these distros just don't work with cable modems? It's not PPPOe, and it's not PPP.  Maybe it's something no one tried to support.

BTW, I'm posting this in two other distros' forums and if I get a solution anywhere I'll post again in all the other forums.

Thanks again, mate :p

---

### Post by mips on 2006-02-01
Yeah, I dunno what I'm still doing here :shock:
If we are in the same time zone then i assume you are in eastern Europe (one of the Slavik countries) ???

You should not need a dialer with a cable modem. 

Could you at least tell me:
1. What Brand & Model cable modem do you use, web link please ?
2. Who is your ISP, web link please ?

This might help you as it is another euro cable modem problem sorted today:
[http://ubuntuforums.org/showthread.php?t=123860](http://ubuntuforums.org/showthread.php?t=123860)

---

### Post by Randux on 2006-02-01
Hey mate,

If I can get to my cable provider's home page then why are we concerned about the modem specifics?  Clearly, it's working.  The issue is- how and where do I specify my ISP's ip address, my userid, and my password?  The cable provider needs to know who to route me to...

P.S.  If I tell you my ISP it won't help; it's all foreign language and you won't get anything out of it :cry:

---

### Post by Randux on 2006-02-01
P.S. I looked at that other thread but I can't understand what's going on, and I don't see any resolution there...did he say it worked?

---

### Post by mips on 2006-02-01
[QUOTE=Randux]Hey mate,

If I can get to my cable provider's home page then why are we concerned about the modem specifics?  Clearly, it's working.  The issue is- how and where do I specify my ISP's ip address, my userid, and my password?  The cable provider needs to know who to route me to...[/QUOTE]

Because i tend to follow a analythical approach and like to know what I'm working with. I cannot answer your questions as I have zero background info to work with.

[QUOTE=Randux]
P.S.  If I tell you my ISP it won't help; it's all foreign language and you won't get anything out of it :cry:[/QUOTE]

Try me, I have a knack for getting info out of foreign language websites :) So just give me the url and I'll have a look. Give me the cable provider as well as the ISP details.

---

### Post by mips on 2006-02-01
[QUOTE=Randux]P.S. I looked at that other thread but I can't understand what's going on, and I don't see any resolution there...did he say it worked?[/QUOTE]

Yes it worked just fine.

---

### Post by Randux on 2006-02-01
I read something that cable modem users have to use a pptp dialer. I'm searching for this now...

---

### Post by Randux on 2006-02-01
Sorry, I didn't see your last posts while I posted just now.

Ok, I warned you :cry: 

netvision.net.il    [ISP]
hot.net.il           [cable provider]

I found some posts from the linux user group here.  Apparently this requires (at least in some cases) a PPTP client which involves more knowledge than I have and more fooling around than I can do this point.  I'm pretty disappointed and this will probably make me go back to windows because I don't think I should have to be a sysadm to connect to the internet!  Something as basic as this should be a very quick process and not require any knowledge.  I have only one machine and I can't browse and read stuff from the internet to troubleshoot while I'm on linux.

---

### Post by mips on 2006-02-01
Give me some time, maybe tomorrow. If I remember correctly I have helped someone setup a cable modem in Israel before, just trying to find the info...

---

### Post by mips on 2006-02-01
Ok, cant fint the post and I'm sure it is not the same as it did not require point-to-point tunneling protocol.

Anway found a very prcise guide to follow, just pay attention to anything related to DEBIAN as the same will apply to ubuntu !!!

[http://www.whatsup.co.il/modules.php?op=modload&name=Reviews&file=index&req=showcontent&id=17](http://www.whatsup.co.il/modules.php?op=modload&name=Reviews&file=index&req=showcontent&id=17)


Hmm, I thought you were in europe, my mistake. Hebrew is definately something I dont have a knack for :)

---

### Post by Randux on 2006-02-01
Brilliant, mate.  Thanks very much.  I'll have a look when the eyes are less groggy.  I was just now downloading some dialers from the ISPs.  But the instructions didn't work and it's easy for me to make mistakes since I know nothing about linux.  Apparently these scripts are expecting some file to exist in /vars/dhcp.  But this directory doesn't seem to exist.  I was just trying this on slax because I can load it to ram and it runs quickly.  Maybe I'll try again on ubuntu when I'm awake.

And I'll call the ISPs during the daytime but I'm not expecting much help.

---

### Post by Randux on 2006-02-02
I found a source for some dialer scripts for linux from one of my two ISPs.  The bad news is that a) the ISP that has the scripts is the one I am going away from and b) I guess I need to be root to install it (which I'm sure is easy but I don't know how to do yet on ubuntu).  In the meantime, I've been trying it on some of the other distros (I especially like Slax) and I think I'm close but since I have no linux knowledge I'm getting stuck on stuff that's probably simple to fix.  I think it has to do with some directory structure assumptions made in the script.

The new ISP which I'll be switching to soon (I'm already set up and can connect from Windows) doesn't support linux and doesn't have any scripts.  The guy tried to be helpful but he thought that VPN was the name of a piece of software and when I asked him which VPN client I should use he went blank.  I don't think those guys are going to be much help.  But I'm hoping that if I can understand what the script does, it should be easy to make it work with the other ISP, since both are set up identically on Windows except for IP address, userid, password.

I just found this: [http://pptpclient.sourceforge.net/howto-ubuntu.phtml](http://pptpclient.sourceforge.net/howto-ubuntu.phtml)

(I am still stuck due to complete lack of linux knowledge and need to do this stuff as root)

---

### Post by mips on 2006-02-02
If you want to execute commands from a terminal as root you simply add **sudo** in front of the command.

---

### Post by Randux on 2006-02-02
Thanks, I'll try it and give you the inevitable error messages :cry:

---

### Post by Randux on 2006-02-02
Instead of me learning how to install VPN...:

I found from our linux user group that we can ask (insist :-# ) that the cable provider use DHCP to gateway us to the ISP like everywhere else in the world. They didn't want to admit it but I got him to say it at the end of the phone call. So now I am waiting for those guys to make my life easy and I won't have to learn how to set up VPN on 10 different live distros.

---

### Post by mips on 2006-02-02
That would be a better option :)

---

### Post by Randux on 2006-02-02
Thanks for all the help.  If I ever get it working, I'll come back and let you know.  I have the thread bookmarked.

:-D

---

### Post by Randux on 2006-02-07
Hi mate,

Ok, I'm posting this from ubuntu :) 

My cable provider and ISP set me up for DHCP, no more VPN.

Is there a firewall on the liveCD?  I don't like the results I got at GRC.COM (ShieldsUp!).  It's a good site for testing.

And I hate firesocks.  It's a POS.  Doesn't anybody make a relatively more private web browser?  

Thanks for your help, just wanted to let you know after all the time you spent.

---

### Post by mips on 2006-02-07
Look at Firestarter or if you want to go deeper, IP tables/Ip Chains.

You can also search this forum for anonimyser etc.

---

