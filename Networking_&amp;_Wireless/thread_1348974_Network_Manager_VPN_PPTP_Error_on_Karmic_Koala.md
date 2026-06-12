---
title: "Network Manager VPN PPTP Error on Karmic Koala"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by ordinaryuser on 2009-12-07
> Hello fellow Ubuntu users and observers,

 I would first like to announce that I have switched part-time (work requires Windows) to Ubuntu Linux. I have one primary desktop and the only operating system is Karmic Koala. Its been a little nerve wrecking at first but I must say, I'm starting to settle in. I've already over come several other challenges through support from users such as yourselves. I look forward to expanding my knowledge on the ins-and-outs of Linux and hopefully contributing in the future. -ordinaryuser I'm having issues connecting to my work VPN via Network Manager w/ PPTP enabled. I'm getting an error every time. Posted below is the background on my situation. I hope I've detailed enough...thanks for reading, I know its long...Please note that this is also posted under [http://ubuntuforums.org/showthread.php?t=964255&page=7](http://ubuntuforums.org/showthread.php?t=964255&page=7) .

**Let it be known I am operating the following:**

OS: Ubuntu 9.10 - Karmic Koala GNOME Version: 2.28.1
USB Wifi Adapter ( TrendNet TEW-229ub)
Network Manager
ndiswrapper w/"windows wireless drivers" to use windows driver for wireless adapter
OpenVPN & PPTP installed into Network Manager
Linksys Wifi Router has VPN>PPTP, L2TP, and the other one...All Enabled.

[B]I have verified my VPN configuration (username/password, host, etc) is correct.

Then this happened:[/B] 
[IMG]http://imgur.com/cCUD5.png[/IMG]

**So then I followed this advice:**

>  i upgraded it to the latest version in the network-manager PPA and it looks like the keyring issues are finally fixed.

Add this to your software sources (system->administration->software sources->third-party software tab):

deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main**After I did that I got this error:**

> W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/") intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 248DD1EEBC8EBFE8**SOOO then I followed new advice same source:**
> Step 1.

Right click nm-applet on your system tray, edit connections.
Click on the vpn tab and add a vpn connection (pptp)

Step 2.
Fill out your usual settings connection name, username, password.

Step 3.
Click advanced.
For your authentication options, untick everything except MSCHAPv2.
Tick Enable Point-to-Point encryption (MPPE).  Leave All Available (Default) selected.
Tick allow stateful encrption.
Click "OK" to save the connection settings and "OK" again on the vpn edit dialog.

Step 4.
Open gconf-editor (alt-f2 and type "gconf-editor").
Under /system/networking/connections you should have a list of all your network connections numbered incremently from 1. If the vpn you created was the latest network connection created it'll be the last one, if not just search for for it (hint: the connection folder should have the id for the vpn connection name you gave in step 2).

Step 5.
Click on the vpn folder and right click, and add a new key.
Add a string named "refuse-eap" with the value of "yes".  
Click "OK" when you're done and close gconf-editor.

Step 6. 

Test your vpn connection.[B]
But at Step 4 I didn't have those folders....[/B]

[IMG]http://imgur.com/Hwoza.png[/IMG]

I can't seem to get it working. Anyone have any advice?

---

### Post by ordinaryuser on 2009-12-07
Ok. I think I solved the first part by simply restarting my machine.

After the reboot I went to select connect to VPN and it started to go through and it prompted me to add to my keyring and I selected always.

Then the icon went through its thing making me think I got connected and then BOOM! A new error. 

My connection still failed!!! 

Also, after rebooting, in the Configuration Editor in /system there is no /network or /vpn directory still....


Please help..

---

### Post by agibby5 on 2009-12-10
I wonder if you have to do this:
> 
Add to /etc/ppp/chap-secrets:

YOUR_DOMAIN_OR_SERVER_NAME\\YOUR_VPN_LOGIN * YOUR_VPN_PASSWORD *Add to 


from here:
[https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN)

---

### Post by ordinaryuser on 2009-12-11
Thanks agibby5 for replying. I was starting to think this thread was lost in the rush of other help requests..

I had already visited the page you suggested. It helped me through part of the problem but still having Failed to Connect issues. I've also tried it using kvpnc (on gnome and kde). Both using the same settings. But along with getting the directories established when trying to connect I get prompted with permission to access the keyring. Which now I no longer get the "no secrets" error. 

But here's my gconf-editor settings for /system/networking/connections/*edited/vpn/
To open gconf-editor >> (ALT + F2) type gconf-editor


**My settings on gconf-editor.** Unticked are PAP, CHAP and EAP
[IMG]http://imgur.com/ouS3H.png[/IMG]

**My settings on network-manager** MPPE is actually ticked w/ 128bit selected
[IMG]http://imgur.com/i1OJx.png[/IMG]

Again, I hope I've been clear enough. I appreciate the support.

---

### Post by Sniffer on 2009-12-17
Hello,

Just to say that i have the same problem,

Connection failed as result....

---

### Post by Sniffer on 2009-12-17
Just to say that i solved this by going old cli way pppd call yourconnection.

If you want to this by the old fashion reply and i make a small tutorial for this.

Again and in 2010 i tought i never need to configure route add and route traffic and create text files with vpn connections.....

And dont want to be a Pain in the *** but last year i said Lin was evolving to something stable and easy to deal with...but now i confess that almost off the stuff is buggy....

---

### Post by agibby5 on 2009-12-17
I was skeptical at first, but I found success with the steps in the following post.
[http://ubuntuforums.org/showpost.php?p=8261958&postcount=6](http://ubuntuforums.org/showpost.php?p=8261958&postcount=6)

---

### Post by Sniffer on 2009-12-17
> **agibby5 said:**
> I was skeptical at first, but I found success with the steps in the following post.
[http://ubuntuforums.org/showpost.php?p=8261958&postcount=6](http://ubuntuforums.org/showpost.php?p=8261958&postcount=6)

It works. Thanks.

At least i avoid the pppd call and the route add , thanks again for the link.

One more workaround, in my count i have already made 5 workarounds on my karmic system....imagine this on a normal, casual user....awesome.

---

