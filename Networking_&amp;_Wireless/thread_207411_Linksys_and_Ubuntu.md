---
title: "Linksys and Ubuntu"
date: 2006-07-01
forum: Networking &amp; Wireless
---

### Post by tripwire45 on 2006-07-01
As I've mentioned in a few other posts, I'm going to hose the Windows XP Pro install on my Dell Inspirion 8200 laptop and install Ubuntu. For wireless networking, the laptop uses a PCMCIA card made by Cisco/Linksys. I know that the Linux kernel can have "issues" supporting wireless cards and tends to favor only certain chipsets. Does anyone have any information regarding Ubuntu supporting Linksys PCMCIA wireless NICs?

Thanks for the help. :)

-Trip

---

### Post by tturrisi on 2006-07-01
Depends on the model number & chipset used in the card.  Most all Linksys will work even if use ndiswrapper w/ windows drivers.  But boot the live cd & see if wifi works or what you need to do to get it to work.  Once all figured out then install to hd.  Were it me I would setup a dual boot.

---

### Post by tripwire45 on 2006-07-01
Thanks for the reply, tturrisi. Your suggestion of using the live CD seems best to test things out first and make sure the various hardware components work and play well with Ubuntu. I'm really not looking to Windows/Ubuntu dual-boot the laptop. I'll keep Windows XP on my lab machine to ensure that my apps that run only on Windows have a place to live. 

I already have a PC that runs Debian but I mainly do http/javascript/xml development on it.  My lab machine has VMWare on it and I run a Debian VM on it as my main "desktop" machine (My main web and mail server runs a Slackware variant).

My laptop is my "production" machine for most of the work I do so I'm moving to a lifestyle where most of my work is done on Linux and not Windows. Natually, I'll have to wean the Missus over time. The kids are going away to uni so I'm sure they'll stick to Windows for the time being.

Thanks again for the help.

---

### Post by tturrisi on 2006-07-02
understood.
I have a similar scene as you except I do most of my dev work on xp, because I am so used to it, but am slowly changing.  I run Ubuntu/XPPro dual boot on my laptop, xppro on my desktop nd I have 2 deb servers, one server is running Woody, php, apache, mysql and a custom web app I built for my construction business (customer db, est forms, etc) and the other server is running sarge & I use it for testing php scripts, web sites, etc.  The sarge server is opened to the wan so I can grab wanted files remotely whenever I want (using ssh). 

I put ubuntu on the laptop because I am now lazy!  I didn't feel like building the system from scratch using a deb net install.  The servers are very lightweight, only fluxbox, emelfm & nedit when I need a gui for something.  I am really liking ubuntu though now that I have trimmed it down & customized it.

The other reason I still use xp for web dev is the graphics & colors are better on my xp installs because linux is still behind windows when it comes to display drivers & graphics rendering.

Also, one can drag a php file to an Internet Explorer window & IE will display the web page whereas if use Firefox one only ever gets a prompt to save the file and one cannot view the html in the php file.  This really sucks when developing web content.  (I don't want to run apache & php on my laptop)

---

