---
title: "resolv.conf clears on reboot"
date: 2006-02-11
forum: Networking &amp; Wireless
---

### Post by Gomek on 2006-02-11
Hello everyone, I'm having a bit of trouble with my DNS configuration.  In case it's important, I've installed dhcpcd since I was having DNS lookup problems (probably related to ipv6).  Searching the forums hasn't given me much help, so I've gotta ask for help!

Every time I boot into Ubuntu, my resolv.conf gets overwritten, forcing me to look up my nameserver and DNS addresses and create a new resolv.conf.  I've heard about changing resolv.conf to read only, but I'd rather not do this unless it's absolutely necessary.  What other things could possibly solve my problem?  A new dhcp client?  A setting somewhere?  A script?

I'd really appreciate some help!

---

### Post by joselin on 2006-02-11
Try this:

> chattr +i /etc/resolv.conf

The file can't be overwritten anymore unless you do the following:

> chattr -i /etc/resolv.conf

For more info:

> man chattr

Cheers

---

### Post by bscbrit on 2006-02-11
Joselin's suggestion may stop the file from being changed, but it doesn't address the 'why'.  Why is the file being changed and by what?  Can you give more details of your hardware e.g. computer type, NIC, connection to ISP etc?

---

### Post by joselin on 2006-02-11
[QUOTE=bscbrit]Joselin's suggestion may stop the file from being changed, but it doesn't address the 'why'.  Why is the file being changed and by what?  Can you give more details of your hardware e.g. computer type, NIC, connection to ISP etc?[/QUOTE]

I know. I use my solution, but i have an static ip address. When i changed network configuration between ethernet and wireless i had the same problem too, so for me works fine. I don't know how dhcp works, because i don't need to use it.

---

### Post by mips on 2006-02-11
The /etc/dhcp3/dhclient-script overwrites the resolve.conf file if the info from dhcp differs from whats in your resolv.conf file.

One solution is:
[http://www.ubuntuforums.org/showthread.php?t=126533](http://www.ubuntuforums.org/showthread.php?t=126533)   Post#17

The easier/better option would be to access your router and manually specify your ISP's DNS servers there. This info will then be passed on via the dhcp ip scope to your PC and the resolv.conf updated with the correct info.

---

### Post by bscbrit on 2006-02-11
But, in that case, why doesn't the dhcp3 script overwrite the resolv.conf with valid information?  The OP is discovering that he has to re-input the DNS server details each time he reboots.

Obviously I will have to do a lot more reading on DHCP - and on most other things related to computers, it would seem! :cry:

---

### Post by Gomek on 2006-02-11
Oh, thanks for the replies, guys!  I'll give you the information you need as soon as I can.  Getting ready for work at the moment!

---

### Post by mips on 2006-02-11
[QUOTE=bscbrit]But, in that case, why doesn't the dhcp3 script overwrite the resolv.conf with valid information?  The OP is discovering that he has to re-input the DNS server details each time he reboots.
[/QUOTE]

Very valid question. In theory all should be well and working. The thing is it does not always work. I can bet you it will work 100% with ms windows. 

When it comes to el-cheapo home gateways and linux things don't always gel so well together. I don't think the problem is with linux but I cannot validate this. One would have to look at whether the tcp/ip stack & utils is implemented 100% according to standards. You never know what they did.

When it comes to product testing they probably only test with windows again.

One way to get a slight glimps into this would be to run a sniffer and look what happens with dhcp/dns request & ack packets etc.

My own pc sometimes battles to get an ip via dhcp so I just use static config instead.

---

### Post by Gomek on 2006-02-11
Alright, back from work.

joselin, I'll try that but I'd like to avoid it if possible.  To me it feels like a workaround instead of a genuine resolution to the matter.  Sure, that might (I haven't checked yet) fix the symptoms, but what's the cause?

bscbrit, it's an AMD64 running wireless on a Netgear MA311 (Prism 2.5 chipset) with a static IP address (specified via my computer).  Wireless router (DHCP enabled)  connected to a cable modem.  The wireless router should know my DNS server information since it displays on the Status page of its configuration tool.

I've tried the information in the link mips provided, but it didn't work.  I've tried commenting out the whole function and just the contents of the function.

---

### Post by Gomek on 2006-02-12
Well, chattr +i /etc/resolv.conf doesn't work I guess because /etc/resolv.conf is a symbolic link to /etc/resolvconf/run/resolv.conf.  I get this error:

chattr: Inappropriate ioctl for device while reading flags on resolv.conf

I'm still at a loss, here!

---

### Post by bscbrit on 2006-02-12
Gomek, I take it that your wireless router is DHCP enabled means that it is getting its IP from your cable modem, and not that it is acting as DHCP server?  If you are using static IPs then it shouldn't need to 'serve' anything.  But, equally, it shouldn't make any difference if it is waiting for a task that will never happen.  And if you are using static IPs, why do you not remove dhcp3-client which appears to be causing your problems?  You mentioned that you were having problems with DNS lookup problems but I don't think that dhcp is going to help here (I fully expect someone with far more knowledge than I to correct me here if I am talking bulls**t again :D ).  Or have I simply misunderstood which problem we are trying to fix?: :-?

---

### Post by Gomek on 2006-02-12
No, it's acting as a DHCP server.  Not all of the computers on the network are using static IPs.  I only set this desktop as static because I'm sharing its printer via CUPS.

If I don't need any DHCP software (such as dhcpcd) since I'm using a static IP address, what do I need to do to connect to the router and to the Internet?

As for you misunderstanding my problem, resolv.conf is being overwritten every reboot, which is a pain.  I am still connected to the network on reboot since I can access my router, but I have to manually write in the DNS information that I'm finding when I access my router.  Quite simply what I want is to not have to manually do anything every reboot.  I want it to not rewrite my resolv.conf on reboot.

---

### Post by stream303 on 2006-02-13
[QUOTE=Gomek]I am still connected to the network on reboot since I can access my router, but I have to manually write in the DNS information that I'm finding when I access my router.  Quite simply what I want is to not have to manually do anything every reboot.  I want it to not rewrite my resolv.conf on reboot.[/QUOTE]

No problem.  There are three different ways to overcome our windows-centric router hardware and to force it to use your known isp nameserver addresses instead of the dns address inside the router.

**Option 1.** Add your known isp nameservers in your router's setup page.

**or**

**Option 2.** Create a working /etc/resolv.conf file with the nameservers of your isp as the **first or only** ones in the list.  Then edit **/etc/dhcp3/dhclient-script** and look inside for the **make_resolv_conf( )** function lines.  Fool dhclient into not overwriting your custom resolv.conf by editing this usually very lengthy function to do nothing:  ( I much prefer option 3 below since dhclient-script does not like typo's!)

[B]make_resolv_conf( )   {
   echo "doing nothing to resolv.conf"
}[/B]

( don't forget the **{ }** braces! )

If you bring your interface down and up again, or just plain reboot, you'll see that your custom resolv.conf stays intact.

**or**

**Option 3.** I don't like editing dhclient-script directly, so the third way is to either **prepend** or **supersede** the resolv.conf file with your known good isp nameservers.

Edit **/etc/dhcp3/dhclient.conf**
  (sudo gedit /etc/dhcp3/dhclient.conf) and just before the "request" line, add this if you want to prepend your isp nameservers and have your routers dns address at the bottom of the list in resolv.conf:

**prepend domain-name-servers 123.45.678.90, 123.45.678.91;**

(For multiple addresses, separate with a comma and don't forget the semicolon at the end)

Reboot or just bring your interface down and up again:
sudo ifdown eth0
sudo ifup eth0

This has been such a problem for my friends running other systems that I've created a little page for it at:
[http://www.greertech.com/nixnotes/dhcpfix.html](http://www.greertech.com/nixnotes/dhcpfix.html)

---

### Post by mips on 2006-02-13
[QUOTE=Gomek]No, it's acting as a DHCP server.  Not all of the computers on the network are using static IPs.  I only set this desktop as static because I'm sharing its printer via CUPS.

If I don't need any DHCP software (such as dhcpcd) since I'm using a static IP address, what do I need to do to connect to the router and to the Internet?
[/QUOTE]


Then you don't need any dhcp server software as bscbrit said. dhcp & dns are two completely separate things.

Just a static config should get you on the net.

---

### Post by Gomek on 2006-02-14
> There are three different ways to overcome our windows-centric router hardware and to force it to use your known isp nameserver addresses instead of the dns address inside the router.
But you see, the dns addresses inside the router are *correct*.  Whenever I reboot, my resolv.conf is reset to an *empty file*.  If it matters any, my Ubuntu laptop works fine.  Just the desktop is having this trouble.  That being said, my make_resolv_conf() looks like this:

make_resolv_conf(){
# ...
}

I also tried "option 3", but I then removed domain-name and domain-name-servers from the request list according to the instructions at [http://ubuntuforums.org/showpost.php?p=685713&postcount=8](http://ubuntuforums.org/showpost.php?p=685713&postcount=8) .

Also, I've removed dhcpcd and it's still clearing on reboot.  This is really frustrating me!

---

### Post by mips on 2006-02-14
I dunno what to say. I do have a suggestion though, compare all the config files between your pc & laptop and see if any of then differ in any way.

---

### Post by bscbrit on 2006-02-14
Disconnect your ethernet connection and reboot the computer.  If the resolv.conf is _still_ corrupted then it is caused by something in your computer and is completely separate from any router influence.  If it is corrupted, we need to identify what is corrupting it.  If it is not the do as mips suggested yesterday, and try a static configuration. It doesn't matter what is in your router, or any other dhcp server, because they simply will not be used.

---

### Post by Gomek on 2006-02-14
> do as mips suggested yesterday, and try a static configuration
I have removed dhcpcd and am using a static IP address.  Is that what you mean?

> Disconnect your ethernet connection and reboot the computer.
I'll do that ASAP and get back to you.

> compare all the config files between your pc & laptop and see if any of then differ in any way.
Oi, I wish I knew enough about what config files might be influencing this.  I guess that's why I'm asking for help!  I'll run through the ones I do know, though.  I do know I've changed the ones on the desktop quite a bit!  Would it be helpful if I posted my config files here?

---

### Post by bscbrit on 2006-02-14
Gomek, we understand your frustration - believe me, we are scratching our heads as much as you are!

I'm not quite sure which configuration files are 'on your desktop' but the files that should be compared include /etc/network/interfaces, /etc/resolv.conf and any of the others that we have asked you to tinker with over the last few days. 

You might also, if you have a dull moment, want to browse through your log files (/var/log/<whatever> to see if there are any clues in there as to what might be happening.  Favourites here would be syslog, messages and dmesg.  I cannot tell you exactly what you are looking for - because we do not know what is happening inside your machine - but I would expect anything that mentions a problem, error and missing doodah to be possibly significant.  :D

---

### Post by Gomek on 2006-02-14
I really appreciate all your help and patience.  Just wanted to update; the resolv.conf does still reset even when the router is off.

In regards to the configuration files, thanks for pointing me in the right direction.  I'll definitely have a look!

---

### Post by Gomek on 2006-02-14
Couldn't find anything in my config or log files, but I'm happy to say that I think I've solved it by installing resolvconf and editing my /etc/network/interfaces file.

---

### Post by bscbrit on 2006-02-14
What exactly did you change to solve the problem?

---

### Post by Gomek on 2006-05-19
Sorry this is such an old thread, but I didn't realize that you asked me how I solved my problem.  Even though this is an old thread, I'm going to answer so that I don't feel like I have unfinished business.

To clarify, my router is DHCP enabled, but I want this specific computer to keep a static IP address.

I have resolvconf installed.  I do not have dhcpcd, pump, or any dhcp software installed, nor do I have dnsmasq installed.

In my /etc/network/interfaces file, I have added the dns-nameservers and dns-search options with their appropriate values under my primary network interface.  I'm not sure if this was needed, but I did it.

Also, something that I am certain no longer matters since I don't use any dhcp client:  my make_resolv_conf() function in my /etc/dhcp3/dhclient script has its body commented out.

---

### Post by bscbrit on 2006-05-19
Thanks for the reply - it might be a bit late but it is always welcome.  Somebody searching the thread might find your solution helpful.

---

### Post by juicybananahead on 2006-06-15
[QUOTE=bscbrit]Thanks for the reply - it might be a bit late but it is always welcome.  Somebody searching the thread might find your solution helpful.[/QUOTE]
Right you were, bscbrit! After I upgraded from Dapper 2.6.15-22-server to 2.6.15-23-server my resolv.conf keep blanking after reboots. The problem was solved by inserting dns-nameservers and dns-search entries underneath eth0 in /etc/network/interfaces

//juicy

---

### Post by juicybananahead on 2006-06-15
[QUOTE=juicybananahead]Right you were, bscbrit! After I upgraded from Dapper 2.6.15-22-server to 2.6.15-23-server my resolv.conf keep blanking after reboots. The problem was solved by inserting dns-nameservers and dns-search entries underneath eth0 in /etc/network/interfaces

//juicy[/QUOTE]
Aha! It seems that it wasn't the kernel upgrade that did the damage, rather it was the installation of the resolvconf package as a dependency when I installed smartmontools. A little bit more info about this in  [Bug #31057]("https://launchpad.net/distros/ubuntu/+source/dhcp3/+bug/31057").

---

### Post by mango.muncher on 2006-10-28
Posting this as post as this post [#13]("http://www.ubuntuforums.org/showpost.php?p=728374&postcount=13") above assisted me and the same problem is bound to occur for someone else upgrading to Edgy Elk 6.10.

I have a dlink 502  and have recently upgraded to Edgy Elk 6.10. After upgrade my correct ISP address was getting replaced by the the DNS of the dlink, 10.1.1.1 which is a common problem with these routers. 

Under Dapper I had commented out the resolv.conf in the dhclient script ([see here]("http://www.ubuntuforums.org/showpost.php?p=1486101&postcount=7")) to fix this problem, but for some reason this did not work for Edgy. The dhclient script was still commented out. 

So I found #13 above and it works a treat.
So thanks.

---

### Post by NoWhereMan on 2007-12-01
Very annoying.

Now, type **sudo network-admin**, go to the dns panel, add them there, then open your **/etc/resolv.conf**. Here's why it's cleared at boot; it DOES work for me :)

---

