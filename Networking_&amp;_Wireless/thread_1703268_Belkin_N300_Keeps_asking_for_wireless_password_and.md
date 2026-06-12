---
title: "Belkin N300 Keeps asking for wireless password and doesn't connect!"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by meddyuk on 2011-03-09
Hiya Guys,
 
I've just literally gone out this  morning and bought the Belkin N300 Dual Band USB for my Deskstation  running Maverick Meerkat. At first i put the stick in and nothing  happened. So i went to System>admin>Windows wireless drivers and  clicked on there. I put the CD in the drive that came with the dongle  and found the drivers folder on the disk. I then installed the .inf file  in the XP folder. It connected straight away as easy as that.
  
I'm really frustrated though as it loses  conectivity and then asks me for my WAP password on connection, but then  doesn't seem to connect. I unplug the dongle and then hit connect again  and it connects. 

If i use the same dongle on XP i have no problems what so ever, so i know its not a signal strength issue.

Any ideas how to make this dongle work without it dropping out.

meddy.

---

### Post by DanneStrat on 2011-03-09
> **meddyuk said:**
> Hiya Guys,
 
I've just literally gone out this  morning and bought the Belkin N300 Dual Band USB for my Deskstation  running Maverick Meerkat. At first i put the stick in and nothing  happened. So i went to System>admin>Windows wireless drivers and  clicked on there. I put the CD in the drive that came with the dongle  and found the drivers folder on the disk. I then installed the .inf file  in the XP folder. It connected straight away as easy as that.
  
I'm really frustrated though as it loses  conectivity and then asks me for my WAP password on connection, but then  doesn't seem to connect. I unplug the dongle and then hit connect again  and it connects. 

If i use the same dongle on XP i have no problems what so ever, so i know its not a signal strength issue.

Any ideas how to make this dongle work without it dropping out.

meddy.

Hi.

I will see if I can help you.

Do this:

Plug your adapter to your pc.

Open a terminal and do:

```
lsusb
```

Post the output.

---

### Post by meddyuk on 2011-03-09
reply on lsusb is as follows:

Bus 003 Device 002: ID 15d9:0a4c Trust International B.V. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:092b Logitech, Inc. Labtec Webcam Plus
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 050d:615a Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by DanneStrat on 2011-03-09
> **meddyuk said:**
> reply on lsusb is as follows:

Bus 003 Device 002: ID 15d9:0a4c Trust International B.V. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:092b Logitech, Inc. Labtec Webcam Plus
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 050d:615a Belkin Components 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I've seen your adapters ID before(050d:615a)

and I think your best bet is to use ndiswrapper.

I will reuse all the relevant info from my old thread.

Before you start following the instructions below

we will start by blacklisting some modules that

can interfere with ndiswrapper.

Open a terminal and do:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

Add these lines to the end of the

file like this:

```

blacklist bcm43xx
blacklist b43
blacklist b43legacy

```

(Note: If you already see "blacklist" lines with these three

modules you don't have to do anything.)

Then save the file(file > save)

and exit. Now you can move on.


First you must get the windows driver.

Save it to your desktop:

[http://cache-www.belkin.com/support/dl/f7d4101%20setup.exe](http://cache-www.belkin.com/support/dl/f7d4101%20setup.exe)


Now we need windows compatibility so we can

extract the specific file needed and for that

we will be using "wine".

If it isn't installed on your computer 

already, go into synaptic and install the

"wine1.2" package.


Next right-click on the .exe you downloaded

and select "open with wine launcher"

or something similar.

Just follow the installation process.


Now launch the "Windows wireless drivers"

program that you used earlier and remove any

previous drivers you've used.

Now select to install a new driver

and navigate to "/home/username/"

Press ctrl+h to show hidden files and folders.

Go to "/.wine/dosdevices/c:/Program Files/Belkin/F7D4101/V1/xp/" 

Install the file called "bcmwlhigh5.inf".

That's it.

Now test your adapter.


Note: If you don't normally use "wine"

and don't need it you can just uninstall it.

Don't forget to make a copy of the "c:/Program Files/Belkin" folder

since you may need it later on if something happens

or you need to reinstall.

---

### Post by meddyuk on 2011-03-09
Cheers mate for such a comprehensive answer. My only query is do i need to go on the Belkin site to get the driver? I already used Ndiswrapper on an old network card, so already used it on this. I installed the Belkin XP driver that came on the disc.

Meddy.

---

### Post by DanneStrat on 2011-03-09
> **meddyuk said:**
> Cheers mate for such a comprehensive answer. My only query is do i need to go on the Belkin site to get the driver? I already used Ndiswrapper on an old network card, so already used it on this. I installed the Belkin XP driver that came on the disc.

Meddy.

I would recommend you get them from the link

I gave you, as I know they worked for another

guy that I helped. Another reason would be that

the driver you get from the manufacturers website

is often newer than the driver you have on the cd.


Good luck and let me know if it works.

---

### Post by meddyuk on 2011-03-19
I went on the link you suggested and it came up with this:

This XML file does not appear to have any style information associated with it. The document tree is shown below.
      
&#8722;
<Error>
<Code>AccessDenied</Code>
<Message>Access Denied</Message>
<RequestId>54241F9DA5A26D05</RequestId>
&#8722;
<HostId>
SblF/W2ssdb0ys3LIY6IuxXcQ3ygUyAdyq1hUzIAijf7+H3MrchvO7SGgEXBBJUo
</HostId>
</Error>

---

### Post by flash63 on 2011-03-19
Hello,
you can use the driver with Ndiswrapper from here. Note the required system version (32bit or 64bit).

[http://forum.ubuntuusers.de/post/2612284/](http://forum.ubuntuusers.de/post/2612284/)

---

### Post by DanneStrat on 2011-03-19
> **meddyuk said:**
> I went on the link you suggested and it came up with this:

This XML file does not appear to have any style information associated with it. The document tree is shown below.
      
&#8722;
<Error>
<Code>AccessDenied</Code>
<Message>Access Denied</Message>
<RequestId>54241F9DA5A26D05</RequestId>
&#8722;
<HostId>
SblF/W2ssdb0ys3LIY6IuxXcQ3ygUyAdyq1hUzIAijf7+H3MrchvO7SGgEXBBJUo
</HostId>
</Error>

Sorry, I did not copy the complete url.

I edited my post above so it should work now.

---

