---
title: "Network-Manager reverts back to Auto eth0"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by GroMmiT on 2010-05-03
Hi,

I'm running Kubuntu 10.4. My problem is that Network Manager keeps defaulting back to Auto eth0. I have created a new wired connection and set my manual addresses. I have ticked the 'connect automatically' button. Every time I reboot or wake up it reverts back to Auto eth0.

I did have wicd installed but this was not reconnecting after wake up (said it was connected but I couldn't ping etc), this is a pain also.

Help??!!


Cheers,

---

### Post by GroMmiT on 2010-05-04
Any clues?

I'm after a solution that will allow me to set a static ip and will reconnect on wake up. Those are the two biggies.



Cheers,

---

### Post by davec64 on 2010-05-04
I've had a similar problem on both my Desktop and Laptop with Lucid, no matter what I did in Metwork Manager I couldn't set up a static IP address. The static address could ping my router but wouldn't return anything from the web.
My solution was to remove Network Manager set the static address manually by editing:

```
sudo gedit /etc/network/interfaces
```

In my case I entered:

```
auto eth0
iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0
network 192.168.1.1
broadcast 192.168.1.255
gateway 192.168.1.1
```

This may work also from wake up.

Certainly worth a try!

---

### Post by Iowan on 2010-05-04
Probably silly question, but...
You DID uncheck "Connect automatically" on Auto eth0?
I suspect Auto eth0 could be modified for a static address.

---

### Post by GroMmiT on 2010-05-05
Thanks for both replies.

I'd prefer to have a network manager working because it's a laptop and  sometimes I need WIFI.

> **Iowan said:**
> Probably silly question, but...
You DID uncheck "Connect automatically" on Auto eth0?
I suspect Auto eth0 could be modified for a static address.

Tell me if this isn't the norm but... There is no 'Auto eth0' when I go to manage connections. Never has been. I know there was in 9.10 but I assumed this must have changed...? Guessing now I'm wrong.

Any reason why Auto eth0 wouldn't show up as an editable wired connection?


Cheers.

---

### Post by Iowan on 2010-05-05
> **GroMmiT said:**
> Any reason why Auto eth0 wouldn't show up as an editable wired connection?:confused:Your "Auto eth0" doesn't show up when you select "Edit connections"? (I'm not running Kubuntu, though...)

---

### Post by GroMmiT on 2010-05-06
> **Iowan said:**
> :confused:Your "Auto eth0" doesn't show up when you select "Edit connections"? (I'm not running Kubuntu, though...)

Correct. I thought it was a little weird too.

That wouldn't be a problem except that it overrides any other connection I try to create...


Thanks again.

---

### Post by s3gfault on 2010-05-06
> **GroMmiT said:**
> Thanks for both replies.

I'd prefer to have a network manager working because it's a laptop and  sometimes I need WIFI.



Tell me if this isn't the norm but... There is no 'Auto eth0' when I go to manage connections. Never has been. I know there was in 9.10 but I assumed this must have changed...? Guessing now I'm wrong.

Any reason why Auto eth0 wouldn't show up as an editable wired connection?


Cheers.
I have the exact same question. hmm.  Doesn't anyone else use static ip addresses?  (to be clear, i don't see Auto eth0 in the wired connection list in knetwork manager either)

---

### Post by GroMmiT on 2010-05-07
> **s3gfault said:**
> I have the exact same question. hmm.  Doesn't anyone else use static ip addresses?  (to be clear, i don't see Auto eth0 in the wired connection list in knetwork manager either)

A friend! ):P

I think there may be something fishy going on here. I know that 'Auto eth0' was editable in 9.10.

Can we get confirmation from another kubuntu 10.4 user that they _have_ 'Auto eth0' in there network manager.

...

---

### Post by ApuX on 2010-05-11
Same problem here. The "auto eth0" is not listed for edition.
Does anybody know the file where the configuration is saved?

/etc/network/interfaces has

auto lo
iface lo inet loopback

---

### Post by tigerstripedcat on 2010-05-12
Yes the kubuntu devs are really dropping the ball on this one.  I think this problem goes back to 9.04 at least: 

[https://bugs.kde.org/show_bug.cgi?id=204340](https://bugs.kde.org/show_bug.cgi?id=204340)

So I finally found a solution here:


[http://ubuntuforums.org/showpost.php?p=8601789&postcount=4](http://ubuntuforums.org/showpost.php?p=8601789&postcount=4)

You might have to restart your computer a few times until you get everything working.  Add a "Static IP" entry, and you can enable the "connect automatically" and "available to all users" checkboxes and uncheck these boxes for the "Auto eth0" entry.

Hope this helps.

---

### Post by GroMmiT on 2010-05-12
> **tigerstripedcat said:**
> Yes the kubuntu devs are really dropping the ball on this one.  I think this problem goes back to 9.04 at least: 

[https://bugs.kde.org/show_bug.cgi?id=204340](https://bugs.kde.org/show_bug.cgi?id=204340)

So I finally found a solution here:


[http://ubuntuforums.org/showpost.php?p=8601789&postcount=4](http://ubuntuforums.org/showpost.php?p=8601789&postcount=4)

You might have to restart your computer a few times until you get everything working.  Add a "Static IP" entry, and you can enable the "connect automatically" and "available to all users" checkboxes and uncheck these boxes for the "Auto eth0" entry.

Hope this helps.

It certainly did help! Thank-you.

I had to reboot after installing gnome-network-manger as there was an error that wouldn't allow it to start..?? After a reboot I could run and edit the connection in gnm then after another reboot it comes up with my static ip under the standard kde nm!

Looks to be all sorted. Thanks again!

---

### Post by real_ate on 2010-08-07
I don't really think that installing the gnome network manager is the *best* or *most stable* way to get this to work in KDE. If anyone has found a workaround for this in the KNetworkManager can they please post it here. 

Also, has anyone filed an Ubuntu/Kubuntu bug for this?

---

### Post by mister_playboy on 2010-09-10
I would also like a fix for this that doesn't involve installing Gnome's network manager.

I assume auto eth0 is being named in some startup script that runs prior to Network Manager and that's why it gets connected first... does anyone know where we would look to find this? Perhaps commenting out a line in a config file would solve the problem.

---

### Post by hornetster on 2010-09-19
I have a similar, "but different" prob... Using Ubuntu 10.04 x86 and have a problem whereby I can see the AUTO for eth0 (DHCP) but want to setup a static, which I have done, and which works if I select it, but on a reboot the AUTO setting is always connected, but I cannot edit ANY settings for it. I have started a thread here ([http://ubuntuforums.org/showthread.php?t=1576412](http://ubuntuforums.org/showthread.php?t=1576412)), but found this and thought I would add my bit.
Thanks, John.

---

### Post by moreTheBeast on 2010-12-08
I have the exact same problem with the version 10.04 of KUBUNTU. I don't like the gnm solution either so any other is very much welcome.
I submitted a bug report yesterday to the KUBUNTU developers page, hope they fix it soon.

---

### Post by Jesus Eguiluz on 2011-03-03
I found a solution, at last for me.

open the file /etc/NetworkManager/nm-system-settings.conf and put the folowing line after "[Main]"

no-auto-default=00:22:15:02:02:5e,

you must put the correct mac for your interface.

restart and now you don't have de "auto eth0" :D

regards.

---

### Post by kirblam on 2011-03-15
@Jesus Eguiluz

Thanks a lot for that tip. I can't believe that a distro would have such a glaring networking error. I'm guessing they haven't caught hell for it because most people are using DHCP - but seriously - a default DHCP interface that hasn't been configured manually *at all* and takes precedence over anything you add in the UI? That's a problem.

Anyway, thanks for the help.

---

