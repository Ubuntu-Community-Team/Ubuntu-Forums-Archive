---
title: "[SOLVED] 802.1x Wireless Corporate Network"
date: 2008-12-12
forum: Networking &amp; Wireless
---

### Post by flatline on 2008-12-12
I just purchased a Dell Inspiron Mini 9.  It came preloaded with Ubuntu 8.04.  I was able to get the netbook onto my corporate wifi with little trouble at all.  I put my cert in, used openssl to generate a .pem, and was able to setup everything through the NetworkManager.  Couldn't believe how easy it was.

However, the kernel that Dell ships with the Mini 9 is intentionally crippled to only allow 1GB of addressable RAM.  I put a 2GB chip into the machine, so I used my home machine to create a LiveUSB and do a clean install of 8.10.  The NetworkManager looks a little different now, and I can't get my Mini to connect to the corporate wireless network anymore.  

One thing I noticed was that previously I was able to manually select "TKIP" as the "Key Type", but this doesn't appear to be an option anymore.  My network uses TLS and TKIP.  The NetworkManager icon in the tray says "Waiting for Network Key for the wireless network 'MY-COMPANYS-SSID'".

Can anyone tell me what might have changed between 8.04 and 8.10, or how to manually configure this?  I was unable to find anything searching through the archives.  Thanks!

---

### Post by flatline on 2008-12-12
I was actually able to figure this out with the help of my buddy Geoff.  It seems that it is indeed an issue with the Intrepid version of NetworkManager.  

Using gconf-editor, we were able to force the connection to use the correct security parameters.  They are located under **/system/networking/connections**.  All of your saved connection profiles will be listed here numbered 1 through n.  My "802-11-wireless-security" record for the network here now looks like this:

```

group       [tkip]
key-mgmt    wpa-eap
name        802-11-wireless-security
pairwise    [tkip]
proto       [wpa]

```

If your network isn't working (especially if it used to under 8.04), I recommend trying this method out.

---

### Post by Favux on 2008-12-13
Hi flatline,

This worked for me!  Details are on the post you cross referenced to here:

   [http://ubuntuforums.org/showthread.php?p=6360321#post6360321]("http://ubuntuforums.org/showthread.php?p=6360321#post6360321")

Thank you.

---

### Post by flatline on 2008-12-13
> **Favux said:**
> I right clicked on the Network Manager applet and went to Edit Connections. I then deleted a duplicate entry and checked the box for automatically connect, since the connection now worked again. I rebooted and the connection failed. Again the password box filled with hex. Again the asking for a password and reconnection.

In the other thread, Favux reminded me of something that slipped my mind when posting earlier.  That is, if this fix works for you, be careful when using NetworkManager in the future.  Almost any changes you make in NetworkManager will cause it to overwrite anything you do in gconf-editor with the default (bad) values.  I don't have a way around this, but as Favux pointed out, there is quite a bit that needs to be worked on with this module anyways.

---

### Post by Favux on 2008-12-13
Hi again flatline,

I noticed in Gconf editor if you right click on a key there are several options. Among them are "set as default" and "set as mandatory".  Could one or the other of these settings block NetworkManager from altering the key? If so which one?

This may be a work around to keep NetworkManager from overwriting Gconf with the default (bad) values.  I don't know enough about Gconf editor and what these options do to risk it.

What do you think?

---

### Post by saywot on 2008-12-14
> All of your saved connection profiles will be listed here

- unless they aren't  !

$sudo gconf-editor 
gives me /System/ 

but no entries for 'network'

---

### Post by james_xxx on 2008-12-14
I would be interested in some possible assistance on this.

The instructions to configure network-manager to connect to the network at my university look like this:

> Configure the settings as follows:

    * Next to "Wireless Security:", select WPA & WPA2 Enterprise.
    * Next to "Authentication:", select Protected EAP (PEAP).
    * Leave the "Anonymous Identity:" field blank.
    * Click the button next to "CA Certificate:", and then browse to the Thawte certificate. If you're using the certificate included with Ubuntu, it will be at: /etc/ssl/certs/Thawte_Premium_Server_CA.pem
    * Next to "PEAP Version:", choose Version 0.
    * Make sure "Inner Authentication:" is set to MSCHAPv2.
    * Next to "User Name:" and "Password:"

As we know, in Intrepid, this isn't working.

Could someone explain to me both how to use gconf-editor, as well as how I might enter these values?

(I am also using a Dell Mini 9.)

---

### Post by james_xxx on 2008-12-14
By the way, saywot, you need to run gconf-editor as user.

I don't actually know how to use gconf-editor, but I found that if you run it as root, you won't see the network configs.

---

### Post by james_xxx on 2008-12-15
If the method of getting a Broadcom wireless adapter to connect to a wpa/wpa2 encrypted network described in this thread actually does work, I would strongly encourage someone to write a howto for use in this forum. From what I can determine, this problem is pretty wide spread in Intrepid, with a half dozen scattered threads on the topic.

It was not obvious to me how to make this solution work in my situation, though I am under the impression that it likely would. Instead, I have taken the chicken's way out, and am successfully using ndiswrapper to access this wpa2 enterprise-encrypted network. I wish I hadn't had to stoop so low, but alas..

---

### Post by Favux on 2008-12-15
Hi james_xxx,

> If the method of getting a Broadcom wireless adapter to connect to a wpa/wpa2 encrypted network described in this thread actually does work, I would strongly encourage someone to write a howto for use in this forum. From what I can determine, this problem is pretty wide spread in Intrepid, with a half dozen scattered threads on the topic.
I strongly agree.  I searched most of those threads.  I worried this thread's title was a little cryptic and wouldn't get enough traffic.  Also the original thread, here:

   [http://ubuntuforums.org/showthread.php?t=963379&page=10]("http://ubuntuforums.org/showthread.php?t=963379&page=10")

where I first came across flatline's solution didn't seem to be paying enough attention.  So I wrote a "demo" thread.  I'm not knowledgeable enough about wireless to write a HOW TO.  The "demo" thread can be found here:

   [http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

Unfortunately it doesn't seem to be getting enough traffic, at least by the folks who have this problem.  Did I pick a bad thread title?  I am open to suggestions.

---

### Post by flatline on 2008-12-15
Thanks for the thanks.  I am by no means a linux expert, I'm just a guy with a lot of curiousity, smart friends, and not much patience for technology.  As far as I can tell, this is how gconf-editor treats mandatory/default parameters: 

[LIST]
[*]*Mandatory* means that the value is considered read-only. I'm not sure if this will prevent a system process like NetworkManager from changing it, but for all intents the value is immutable.
[*]*Default* means just that - the value which should be defaulted to, but can be changed.
[/LIST]

I will make a note to test out the *mandatory* param later to see if it will prevent NetworkManager from messing up the settings again.

I would be willing to help out however is needed.  I realized after posting the thread that the title probably wasn't the greatest, but those were the terms I was searching for in my particular instance, and it doesn't seem like you can change a thread title after the fact.

In addition to not being a linux expert, nor am I an expert in wireless security.  However, **james_xxx**, could you post the details of your connection's '802-11-wireless-security' from gconf-editor?  May help shed some light on just what problems this solution is viable for.

---

### Post by Favux on 2008-12-15
Hi flatline,

I know, I tried to change a thread title too.  I look forward to the results of making the keys mandatory in gconf.  If positive I will try it and see if I can duplicate them.  Like I've been saying any help is appreciated and you've already been more help on wireless than anyone else!

james_xxx if you would post your gconf details, that would be good.

---

### Post by BitJockey on 2009-04-19
Running Dells 8.04 version. Config doesn't show "Connections" but id does have a drill down directory the shows the network (System\Networking\Wireless\Networks\networkname).

In the networkname there are 6 attributes: bssids, essid, timestamp, we_cipher, wpa_psk_key_mgt, wpa_psk_wpa_version. Any information on what the values should be for the last three?

bssids:              mac address of my router
essid:               networkname
timestamp:           self explaining
we_cipher:           4
wpa_psk_key_mgt:     2
wpa_psk_wpa_version: 2

Thx,
BitJockey

---

### Post by keplerspeed on 2009-06-09
Flatline, cheers. Using gconf-editor did the trick.

For me I had a look at /var/log/syslog, and it said that it was setting the "scan_ssid" key to a value of 1. However, my hidden ESSID network requires a scan_ssid of 2 (1=broadcasted, 2=non broadcast).

SO, under networks in gconf-editor i added scan_ssid with a value of 2. And now I have wireless.

For me, I had no issues with broadcasted essid networks, but bad for hidden ones. Seems like network manager is misbehaving.

---

### Post by flatline on 2009-07-07
I don't know if anyone is still reading this thread, but I haven't updated to Jaunty (9.04) yet, so I was wondering if the same problems are persisting.  I am assuming NetworkManager has not yet undergone a complete overhaul?

---

