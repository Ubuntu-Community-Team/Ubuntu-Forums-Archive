---
title: "speedTouch 530i router"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by plusangel on 2006-06-07
Since is my first post…I’d like to express my happiness that I found such an active community and such a brilliant distro.:-D 

I’ve limited experience in linux (mainly from suse) but I’m willing to learn a lot!

I have used the live cd 6.06 to check main and important issues.
First of all the internet connectivity.

I have an aDSL connection using a Thomson SpeedTouch router 530i.

This is working fine in windows.  As far as I remember is set at PPPoA (as my ISP provider instructed me).

In 6.06 environment, I’ve opened the networking tab
Insert my static IP 10.0.0.139 (255.255.255.0)
		Getaway 10.0.0.138
And I’ve set my ISP’s name servers in DNS tab.

Then I’ve opened the firefox browser but nothing.:( 
I’ve typed a URL and at status bar informed me that “looking foe www…..”

I’ve typed in URL address of the browser the router’s IP 10.0.0.138 – nothing again ](*,) 

I’m afraid that something is wrong with the 2 Ethernet ports in my ASUS motherboard.  I will try an INTEL gigabit adapter.

Has anyone else use this adsl router?
Is something that I miss in the procedure that I described?
Do you need more info about my system to help me?

TIA

---

### Post by trosk on 2006-06-07
Have the same prob. with a speedtouch 546T. ](*,) 
Have to open terminal and write "sudo dhclient" in order to go online.
Havent found any way around this so fare...:confused: 
trosk

---

### Post by plusangel on 2006-06-07
ok, you mean that&#8230;

**although** from the networking parameters&#8217; tab &#8211; you have deactivate the dhcp client feature and you have used the Static IP address 10.0.0.139 for your box

 &#8211;> 

in order to go online you have to type in the terminal &#8220;sudo dhclient&#8221; ?

---

### Post by trosk on 2006-06-07
The onely way to not be offline is what I said in topic abov.
I'v tryed almost every solution on this forun, but no.  ](*,) 
Running Nvidia nforce 3. 250
This is not the way it should be, but doeing the best i can at the moment.
Sorry to said but can't do bether.
It's onely 4 mnd. sines I started with linux "ubuntu". It was workinh 100% , with 5.10. but when I upgraded to "dapper" everything whent down.
Whish I knew the way back to breezy..5.10.  yeh I know, but then i'm looseing everything on my ubuntu.
This is a bad releas in my eyes......No network.. working....:twisted:

---

### Post by plusangel on 2006-06-08
I found this [article]("http://www.greertech.com/nixnotes/dhcpfix.html") 
By searching “sudo dhclient” command…I don’t know if it helps!

---

### Post by mips on 2006-06-08
Disable IPv6 globally and see what happens.

---

### Post by plusangel on 2006-06-08
Problem solved…

Seems that I messed up the settings between the 2 on-board Ethernet adapters.

Everything is fine now…

---

