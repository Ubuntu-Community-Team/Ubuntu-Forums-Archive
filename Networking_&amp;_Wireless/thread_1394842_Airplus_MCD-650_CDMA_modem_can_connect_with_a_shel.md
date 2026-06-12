---
title: "Airplus MCD-650 CDMA modem: can connect with a shell script but not NetworkManager"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by temcat on 2010-01-31
Hi all,

I have Ubuntu 9.10 with the latest updates. My Airplus MCD-650 CDMA modem is detected and can connect with the shell script I've quoted below. However, I can't make it to connect using Network Manager. It may have to do with login and password (according to my Windows setup, it's "mobile" & "internet") - but what's puzzling, I can't see any traces of login and password in the script which nevertheless connects successfully. How do I troubleshoot this NetworkManager connection failure? Has anybody had a similar problem?

My connection script:
```
        #!/bin/sh
        mknod /dev/ppp c 108 0
        DIALTIMEOUT=20
        MODEM=ttyUSB0 SPEED=921600 MODEM_INIT='"AT+CRM=1;&C2" OK'
        IH_IP=" ipcp-accept-local ipcp-accept-remote noipdefault
        debug usepeerdns user mobile mtu 1400
        novj nobsdcomp novjccomp nopcomp noaccomp"
        LOGSCRIPT="CONNECT"
        PHONE="#777"

        # delete default route before launch
        # and restore it when done
        DR=`route -n | egrep '^0.0.0.0'| grep -v ppp | sed 's/^[^ ]*  *\([^ ]*\) .*/default gw \1/'` ;
         if [ -n "$DR" ] ; then
           trap "echo route add $DR ; route add $DR ; exit"  2 3 9 15
            route delete $DR
            echo route delete $DR
         fi

        ########## Restart pppd if connection is broken ########
        while  true ; do
            pppd \
            connect 'chat -v ABORT "NO DIALTONE" ABORT "NO CARRIER" ABORT BUSY "" '"$MODEM_INIT"' ATDP'$PHONE' '"$LOGSCRIPT"' ;' \
            crtscts defaultroute modem -detach mru 1400 \
            $NASH_IP:$IH_IP /dev/$MODEM $SPEED
            cat /etc/ppp/resolv.conf > /etc/resolv.conf
            sleep $DIALTIMEOUT
        done
```

---

### Post by pdc on 2010-01-31
hi;

one can bypass network manager successfully by using the programme wvdial; 

[http://en.wikipedia.org/wiki/Wvdial](http://en.wikipedia.org/wiki/Wvdial)

it also seems avoid the need for chat scripts and other things

[http://ubuntuforums.org/showthread.php?t=1393348](http://ubuntuforums.org/showthread.php?t=1393348)

in this post, it worked for someone yesterday; as you are a CDMA user, I see your phone number is the usual CDMA number of #777

---

### Post by temcat on 2010-01-31
> **pdc said:**
> hi;

one can bypass network manager successfully by using the programme wvdial; 

[http://en.wikipedia.org/wiki/Wvdial](http://en.wikipedia.org/wiki/Wvdial)

it also seems avoid the need for chat scripts and other things

[http://ubuntuforums.org/showthread.php?t=1393348](http://ubuntuforums.org/showthread.php?t=1393348)

in this post, it worked for someone yesterday; as you are a CDMA user, I see your phone number is the usual CDMA number of #777

Thank you, pdc. I know that I can use wvdial, too - I just hoped there were a way to manage all my connections from within NM, as it should be. The script works well, it even gives me better speed than in Windows for some reason.

---

### Post by temcat on 2010-02-01
Update: I tried it in Fedora 12 LXDE respin, and could connect automatically using NetworkManager (after modprobing the modem manually).
Also, connection via NetworkManager doesn't work in Lucid.

---

### Post by alexfish on 2010-02-01
hi

could you post more details about the problems you are having with the network manager.

RE: Ubuntu 9.10 only

if you have problems with this Network Manager , Like A Lot of people , you are not alone

Continue using wvdial , also try installing Gnome ppp , it will do the same as wvdial but works from the front end

Thanks in advance

alexfish

---

### Post by pdc on 2010-02-02
thanks temcat;

curious the subtle differences in the latest distros;

I find Fedora 12 works for me with a Vodafone K3565-Z modem; 

(whereas others: , Ubuntu, Mandriva) ..... do not ..........

curiously, the blue flashing light of the K3565-Z works on Fedora; in other distros, it gives a red flashing light and will not connect; curious what it is in the startup sequence that correctly activates the blue flashing light;

---

### Post by temcat on 2010-02-02
> **alexfish said:**
> hi

could you post more details about the problems you are having with the network manager.



Well, after creating a connection, I click it in the NM, and after a minute or two of throbbing it stops trying to connect, and a notification appears that I'm disconnected.

In the logs, I see something about unknown error 100 and about my modem not supporting +CMEE command.

---

### Post by alexfish on 2010-02-02
> **temcat said:**
> Well, after creating a connection, I click it in the NM, and after a minute or two of throbbing it stops trying to connect, and a notification appears that I'm disconnected.

In the logs, I see something about unknown error 100 and about my modem not supporting +CMEE command.

RE:Network Manager Connections

Extract from site

                                 **Future Improvements**
 There&#8217;s a few things we can do in the future&#8230; If the connection fails for some reason, re-display the Assistant.We can autodetect your provider based on the first 5 or 6 digits of your IMSI on your SIM, skip the Country page, and automatically select that provider in the Provider page, saving you a step or two.Unfortunately, we can&#8217;t autodetect the plan/APN because that&#8217;s not stored anywhere (well it is usually preloaded into your phone, but *all* the APNs are, and there&#8217;s no indication of which one is the one you really want).So there&#8217;s room to make it even more awesome.
 **Your help is required**
 Again, the mobile broadband provider database is incomplete. [Help fix it]("http://bugzilla.gnome.org/enter_bug.cgi?product=NetworkManager") up for your country and your provider by filing a bug with your information.Include your provider name, your country, your plan&#8217;s marketing name if you know it, and of course the APN you&#8217;re using for data. If you have a CDMA provider, just tell us your country and provider name. Username and password are generally ignored by the network and the device, so they aren&#8217;t useful. It&#8217;s your help that makes this effort work better for everyone.

 [http://blogs.gnome.org/dcbw/2009/06/22/mobile-broadband-assistant-makes-it-easy/](http://blogs.gnome.org/dcbw/2009/06/22/mobile-broadband-assistant-makes-it-easy/)

My comment
can only add ; A method to link  NM  user Scripts would be handy ;  These scripts could be supplied by the device

---

### Post by alexfish on 2010-02-09
hi

I have received  PM from temcat , saying this device  is working in Jaunty :

also wondering and assuming that you can get connected,  updating to the latest kernel for Karmic would help

I have traced where the info for NM wizard is kept in 9.10. will be dropping back to Jaunty to compare the Two files; hopefully report back soon

---

### Post by temcat on 2010-02-19
OK as alexfish asked, I describe what it took to make the modem work in Jaunty (on which I'm settled now).

First, the modem is not recognized automatically, so you have to do

```
sudo modprobe usbserial vendor=0x1011 product=0x3198
```

in the terminal. Also, to get the module automatically load on boot, put the same line without "sudo" in /etc/rc.local file.

After that, in Jaunty I just had to go to the Mobile Broadband tab of NM's Edit Connections dialog, select my provider and enter the right username and password. It connects without problems. The only problem is that it won't simply connect again after disconnecting - you have to unplug and replug you modem first.

---

