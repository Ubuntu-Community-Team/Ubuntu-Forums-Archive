---
title: "Confusing issues with networking - ripping hair out"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by PCDoc on 2009-01-14
Hi guys, I've got a bit of a problem I've been bashing away at for two days using nothing but trial, error and google and I can't seem to get anywhere.
This may get a little long because I'm going to try and be as descriptive as I can so that I can eliminte things already tried so please bare with me.

I run a small pc repair service with my father in law from a room in the house upstairs.
Downstairs in the loung is where the main and only Virgin / NTL / Telewest modem is located we have a wireless router and a lynksys router.
I'll explain how and why now.

Our business telephone line is provided by Vonage, an internet phone provider. They supplied us with the Lynksys router which has 4 LAN ports and 2 Phone ports on.
We originally had this connected to the Virgin modem and then to the pc, but as we needed internet access upstairs, we purchased a wireless router to add in line.

So now we have the Wireless router connected to the modem then from the wireless router we are connected to the lynksys router via ethernet cables.

This all works perfectly, we get internet downstairs via the pc thats etherneted to the lynksys, the phone works and the wireless is sent upstairs perfectly, so the whole thing works.

To test it, I took my laptop which is running XP upstairs and connected to it wirelessly using my Raling USB Dongle. I got the internet fine, no problems.

But my problem lies with the ubuntu box we have built upstairs which we are going to be using as a firewall and general file server for the workshop.

I purchased a Ralink run of the mill pci wifi card and fitted it in the ubuntu box.
This detects fine and runs good. It connects and we get internet on it.
Now what I am planning to do is...

Connect the ubuntu box by ethernet to a wired router upstairs and connect other pc's to that router and use the ubuntu box like a gateway and share its connection across the wired network upstairs.

But it's giving me some real grief.

I get the wireless connected and get internet but then when I plug the lan in thats detected and connected and it wipes out the wifi.
The wifi is connected but I lose internet completely.
I can ping the wifi router downstairs but not much else.

How can I route connections coming in via the router to the ubuntu box by its ethernet so that it shares the internet?

I've tried firestarter firewall however I select my wifi connection or wlan0 as it says in ubuntu as my internet connection, then I select eth0 when it askes me what I'm sharing, and when I start the fire wall, an unknown error occurs.
I've tried disabling enable DHCP in the firestarter setup wizard, but nothing works.

My heads spinning from it all lolz.
I can't blame ubuntu, because I know it's a problem caused by my lack of understanding of linux and ubuntu.

One of the main reasons as well we chose ubuntu for the gateway / ICS box upstairs was so we could explore linux and get to know it.
After all, what kind of computer techies would we be if we wern't willing to explore and learn.
But I admit it, this one's got me beat.

I've looked into bridging but I could do with a real n00b guide on doing it. That was the reason I tried firestarter.. Google results came up with it so I thought I would give it a go.

Sorry it's such a long post, but I want to be accurate and helpful.

Many many many thanks to anyone who can help.

---

### Post by dmizer on 2009-01-15
What it seems as though you would like to do is called ICS?

First, I suggest you ditch Firestarter. Then, take a look at this wiki (make sure you configure your wired connection on a different subnet from your wireless): [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

Is there a specific reason why you need a firewall between your upstairs network and your wirless router? I ask because there may be an easier way (binding interfaces) to secure the server from wireless encroachment.

---

### Post by PCDoc on 2009-01-15
Hi Dmizer, Many thanks for replying.

I was thinking of using a linux box on the upstairs network as additional security.
We're more than likely going to be having customers machines hooked up to the network for internet access and such so we thought we would be extra careful and get a firewall style box up and running.
Also the linux box will be acting like a central file server where we can store ghost images and such.

We don't want to risk a customers machine on an open network so we thought this a good idea.
Plus it gives us a chance to get to work with linux.

Now I know theres a fair chance something nasty wont penetrate the wired side of the router set up downstairs, so most things using cabled lan down their should be okay, but it's the wifi side upstairs we're bothered about.
Specifically the wifi connection between the wireless router downstairs and the wireless card on the linux box upstairs.
Encryptions can be broken and networks hacked as we've all seen so something between the shared (if I can get it to work) wifi internet connection and any customers machines and/or our own must be a good thing.

The wired router (that's connected to the linux box to its one and only ethernet card) which we are trying to share the conenction with, has a firewall built in so there is some protection within the upstairs router, but I don't feel that alone would be enough.

Or am I going over protective?

Thanks again!

Mike.

EDIT: I didn't get a chance to have a go at it today, I was helping a buddy of mine with some PC2-8500 (1066Mhz) ram he had brought for his Abit AX78 board.
We just can't get it to run stable no matter what suggested ideas and settings we try.
So I, well we, were busy with that for a good few hours lol.

I'm planning to have another stab at the linux box again tomorow though.
I'll look into the link you posted. I've emailed a bunch of searched posts to myself so I can call them up on the laptop while trying to resolve this tomorow and this post is amongst them.

---

### Post by dmizer on 2009-01-15
Okay ... let me see if I understand your setup correctly.

You have something like this:

Internet <=> modem -> wirless router ~~> upstairs ubuntu -> rest of upstairs network

If that's the case, then all you need to do is bind interfaces. For example, when you configure samba, bind it to the wired interface, so nothing from the wireless side can see the samba shares. You can do this with any protocol: CUPS (printer sharing), NFS, FTP ... and it's much easier to configure things that way than trying to figure out IPtables.

Assuming that wlan0 is your wireless interface and eth0 is your wired interface, here is an example smb.conf that would prevent anyone from accessing your files over wireless:
```
[global]
    ; General server settings
    netbios name = YOUR_HOSTNAME
    workgroup = YOUR_WORKGROUP
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192

    passdb backend = tdbsam
    security = share
    name resolve order = hosts wins bcast
    wins support = no
[B]    bind interfaces only = yes
    interfaces = eth0[/B]

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

[MyFiles]
    path = /path/to/share/
    browseable = yes
    read only = no
    guest ok = yes
    create mask = 0644
    directory mask = 0755
    force user = UBUNTU_USERNAME
```
(above smb.conf file taken from the samba server howto in my sig)

Those two bold lines mean that samba will only communicate on the eth0 interface. Anything attempting to access over wireless will be ignored.

Since you must configure samba anyway, it's a simple matter of adding those two small bold lines in order to keep wireless traffic from your files. Much much easier than confgiuring IP tables.

More information here: [http://samba.org/~tpot/articles/multiple-interfaces.html](http://samba.org/~tpot/articles/multiple-interfaces.html)

There is some discussion here on how to configure samba and IP tables to work together: [http://troy.jdmz.net/samba/fw/](http://troy.jdmz.net/samba/fw/)

Binding protocols to your wired interface takes all the guesswork out of securing your server.

---

### Post by PCDoc on 2009-01-18
Hi again,

Well, nothing I'm trying is working.

The main problem at the minute is that the lan connection completely kills the wifi.

When I boot up ubuntu, I have no internet connection on the box at all.
The instant I go in to the connections manager and delet the auto eth0 connection, the internet comes on.

Then I try and add the eth0 back, and the internet is dead again.
Seems the two conflict.

Is ubuntu not capable of managing more than one connection?

I dont know if this is a reason or not but the ethernet is onboard the motherboard, where as the wlan (wifi) is a pci card.
Should this matter???


I tried following that samba guide and i've even tried IP tables and adding a bridge, but nothing is sucessful while lan conflicts with wifi.
I cant get the two to stay connected without lan interfering with the wifi.

Thanks again,

Mike

---

### Post by dmizer on 2009-01-18
Ubuntu is perfectly capable of managing more than one connection. As of this writing, NetworkManager is not capable of managing more than one connection.

Install gnome-network-admin via synaptic or the cli.

Then, disable network manager by adding the following lines to /etc/rc.local (before "exit 0"):
```
/etc/init.d/NetworkManager stop
killall nm-system-settings
```

After that, you can manage your network cards under system > administration > network

---

### Post by blothian on 2009-01-18
**_[CENTER]I have Talktalk broadband with a Linksys WAG54GS Wireless router[/CENTER]_**
Phone Line -> Linksys-> Ethernet -> Compaq
                     -> Wireless -> Toshiba Laptop
                              -> Fujitsu Siemens Laptop
                              -> Dell Laptop
                              -> Compaq (Ubuntu) w/ Linksys WUSB54G

All i did was find out if my broadband was RFC 2516 PPPoE or otherGot the username & password save, setup wireless with pass and name for network.  ->  On every computer changed the workgroup to ******* NETWORK then on vista computers Enabled all sharing with no password then same for everything on the network, I can also connect to Windows Media Center thru my Xbox 360 with no problems.
Hope this helps!
Benjamin

---

### Post by PCDoc on 2009-01-18
Cheers guys, I'll try those things when the kids are in bed.
I've brought the server home for the weekend to work on and I have the same kind of setup as we do at my father in laws upstairs room.

So when I get some quiet time, I'll do some more experimenting.
Must be 5 days I've been working on this and I'm not giving in till it rolls over and plays ball lol.

Thanks again guys!

Mike.

---

### Post by PCDoc on 2009-01-18
I did as you suggested dmizer however now there is no option for tkip2 encryption just WEP.

Anything else I could try... another type of network management perhaps?

---

### Post by PCDoc on 2009-01-18
Well this is driving me loco.

Tried wpa_supplicant to try and get wpa2 and still nothing but errors.

---

### Post by dmizer on 2009-01-18
> **PCDoc said:**
> Well this is driving me loco.

Tried wpa_supplicant to try and get wpa2 and still nothing but errors.

For WPA, take a look at this thread: [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

### Post by PCDoc on 2009-01-18
Thanks again dmizer, that's helped a great deal.

Now, I've managed to connect, well sort of.

What I have now is at boot up, ubuntu slows about half way then goes into the post screen and shows it has ran wpa_supplicant and is looking for a DHCP address but comes back with none.
Ubuntu then boots up but there is no network.

I have to go to var/run and kill the process id for wpa_supplicant.wlan0.pid and then go to terminal and run 
```

sudo wpa_supplicant -d -c/etc/wpa_supplicant.conf -iwlan0 -Dwext
```

and then run sudo dhcpclient wlan0

Then and only then does it conect.

I've been at this for hours and I'm beat, it's 2:30am and I need some sleep.

If you could shed some light, that would be good.

Here is my wpa_supplicant.conf

```

ctrl_interface=/var/run/wpa_supplicant
#ap_scan=1

network={
       ssid="myssidhere"
       scan_ssid=1
       proto=RSN
       key_mgmt=WPA-PSK
       pairwise=CCMP TKIP
       group=CCMP TKIP
       psk="mypasskey"
}

```

and my interfaces file is like this:

```

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet dhcp
wpa-driver wext
wpa-ssid myssidhere
wpa-ap-scan 1
wpa-proto RSN
wpa-pairwise CCMP
wpa-group CCMP
wpa-key-mgmt WPA-PSK
wpa-psk 8b79c14a1311970##############################
pre-up wpa_supplicant -Dwext -wlan0 -BW -c/etc/wpa_supplicant wpa_supplicant.conf post-down killall -q wpa_supplicant

```


I also created wireless-network.sh  and added /etc/init.d/networking restart 
like the guide you gave me said to do.

Maybe I've missed something, or something is conflicting.

I've made sure that network manager is dissabled so its not that.

It's very late and im not thinking straight now.
Its taken all night to get this far lol.

Thanks again!!!

---

### Post by dmizer on 2009-01-19
No problem, but I have zero experience with WPA. Unfortunately, I haven't managed to get my hands on a WPA wireless router here (mostly because I don't really need one).

I suggest you repost the above in the WPA howto thread for better help than I will be able to provide :)

---

### Post by PCDoc on 2009-01-19
Thanks dmizer, you have been a BIG help, truly you have.
Without your pointers in the right direction I would still be fumbling about without a connection.

At least I can connect to the internet now without the use of NetworkManager so that's a big step in the right direction.

All I need to do now is find out why it wont do it automatially, un-aided at startup.

Coo, the temptation to use windows was getting strong at one point, but the lure of linux being more secure for the job kept me going.

I know windows inside and out and it's soooo much easier, a few clicks and you're done but on the other hand it's even easier to get infected.

Again, many thanks for all your help, patience and advice.

:guitar:

---

### Post by dmizer on 2009-01-19
> **PCDoc said:**
> Thanks dmizer, you have been a BIG help, truly you have.
Without your pointers in the right direction I would still be fumbling about without a connection.
My pleasure. Keep us updated and let us know when you get everything working correctly :)

> **PCDoc said:**
> Coo, the temptation to use windows was getting strong at one point, but the lure of linux being more secure for the job kept me going.

I know windows inside and out and it's soooo much easier, a few clicks and you're done but on the other hand it's even easier to get infected.
Truthfully, some things are most certainly easier in Windows. But, sometimes things are easier in Windows only because you "know windows inside and out." It's been about 5 years since I've done any Windows configuration, and I'm sure I would have a great deal of difficulty making Windows do what you're trying to do. :???:

Anyway, it's always nice to give help to someone who sticks to it :guitar:

---

