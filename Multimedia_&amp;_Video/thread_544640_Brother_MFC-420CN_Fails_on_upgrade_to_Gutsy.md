---
title: "Brother MFC-420CN Fails on upgrade to Gutsy"
date: 2007-09-06
forum: Multimedia &amp; Video
---

### Post by mobian on 2007-09-06
I've got a Brother MFC-420CN installed via network interface on my local LAN. I had this installed and working perfectly. I upgraded to Gutsy 7.10 this weekend, and now it will no longer print. I have tried removing the printer, and reinstalling everything from scratch, but it still fails. 

I enabled debugging in cups, and noticed that filter provided by brother is spitting out some sort of error about "Operation Not Permitted".  On a hunch, I tried catting a file into the filter, then piping that into lpr directly, and doing that I am able to get it to print. So something is messed up in this filter and how it's interacting with the newest setup on Gutsy.

Anyone have any success with this printer after an upgrade to Gutsy ??

Thanks!

---

### Post by mobian on 2007-09-06
Just another comment here, the strange thing is in cups if I go look at the job, it says it completed successfully. However, under the "Pages" column, it says "Unknown". When I manually pipe a text file into the filter, then pipe that into lpr, it prints, and the pages column correctly shows how many pages it was. So this must be affecting this somehow.....

---

### Post by zobojoe on 2007-10-19
Hi - I have just had the same experience - was running with a MFC-420CN on 7.06 quite happily until I did upgrade today and now nothing ! - arrgghhhh - did you ever find a solution ?

---

### Post by mobian on 2007-10-19
Actually, I was able to finally get this working.  I did several things, but none of them seemed to solve the problem until I did a:

> 
apt-get update && apt-get upgrade


And then I rebooted, and magically it started working again.  I _DO_ think I had to remove the printer and re-add it though to get it working, I can't recall.

I saw several other links in these forums with other ideas which may or may not help, but I'll put them here anyhow to save you some searching:

```

sudo aa-complain cupsd

```

That didn't seem to solve the problem, but maybe it's because I didn't restart cups, or because I needed to reboot or something, not sure.  So then I saw this other post instructing me to do this:

Try editing /etc/apparmor.d/usr.sbin.cupsd to add the following lines:

```

   # Brother printer drivers are installed in /usr/local
   /usr/local/Brother/inf/brMFC210Cfunc r,
   /usr/local/Brother/lpd/filterMFC210C ix,
   # And need read acces to /dev/tty
   /dev/tty r,


```

Then restart: /etc/init.d/apparmor reload 

Anyhow, good luck!

---

### Post by zobojoe on 2007-10-20
I shall post a big smile if and when I get this working but you have already saved me hours of searching existing posts - tyvm indeed

---

### Post by froy02 on 2007-10-20
Here's  he website for installing the drivers for Brother mfc printers.

[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html)
The lpr driver MUST be installed first then the cups driver.  Then change the setting by opening firefox with "http://localhost:631".  Choose the printer tab and check if it is  configured properly if not configure it. 
My MFC665cw has this configuration showing on firefox browser:

Description: MFC665CW
Location: Downstairs
Printer Driver: Brother MFC-665CW CUPS v1.1
Printer State: idle, accepting jobs, published.
Device URI: socket://192.168.000.100

The device URI (socket://192.168.000.100) is the ip address of my printer.
Yours may be different o substitute your own printer ip address.

If your printer is not configured properly follow the instructions in setting it up.  If the driver does not show in the list that comes up find it and select it as the driver to use.  I used gdebi installer to install the lpr and cups drivers.

---

### Post by zobojoe on 2007-10-20
:) - All working again !

Before re-installing the LPR and CUPS I tried the few suggestions you had made but none seemed to hit the spot so I followed [http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html](http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html) and hey presto !

Many thanks for your help - I love Ubuntu but without the help I get from these Forums (or is it Fora ?) like would be more challanging !

Thanks again

---

