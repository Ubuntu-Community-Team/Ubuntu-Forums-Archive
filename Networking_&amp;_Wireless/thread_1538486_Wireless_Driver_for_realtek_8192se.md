---
title: "Wireless Driver for realtek 8192se"
date: 2010-07-25
forum: Networking &amp; Wireless
---

### Post by mett demon on 2010-07-25
Hi everyone,
I am using ubuntu 10.04lts on my compaq615 laptop, which has a realtek wireless card, with which I had a few issues to get it to work. 
Here is what I had to do:
download the drivers from realtek webpage, 
unzip to desktop,
cd (realtek file on desktop)
make clean
make
make install
modprobe r8192se_pci
exit
 
when I do this, it works beautifully, after setting my router to open I may add. 
So, as I said it is probably the fastest wireless I have ever experienced, but my problem is this, everytime I switch my laptop on I have to re-install, starting at:
cd (realtek file on desktop)
make clean
make
make install
modprobe r8192se_pci
exit
 
Any help for this noob, anyone???

---

### Post by mett demon on 2010-07-26
no-one able to help me?  

:confused:

---

### Post by mhgsys on 2010-07-26
try adding r8192se_pci to /etc/modules

```
gksudo gedit /etc/modules
```

---

### Post by mett demon on 2010-07-27
:D

you, my friend, are a gentleman and a scholar.
Did as you advised and is working beautifully.
Thanks, thread resolved, hope this will be of use to everyone with the same issue.

---

### Post by mhgsys on 2010-07-27
;)

You're absolutely welcome

---

### Post by Kundalinux on 2010-07-27
> **mett demon said:**
> Hi everyone,
I am using ubuntu 10.04lts on my compaq615 laptop, which has a realtek wireless card, with which I had a few issues to get it to work. 
Here is what I had to do:
download the drivers from realtek webpage, 
unzip to desktop,
cd (realtek file on desktop)
make clean
make
make install
modprobe r8192se_pci
exit
 
when I do this, it works beautifully, after setting my router to open I may add. 
So, as I said it is probably the fastest wireless I have ever experienced, but my problem is this, everytime I switch my laptop on I have to re-install, starting at:
cd (realtek file on desktop)
make clean
make
make install
modprobe r8192se_pci
exit
 
Any help for this noob, anyone???

Hi,

Could you give us the complete command lines for those not too familiar with Terminal? I'd appreciate it. Thanks

---

### Post by mett demon on 2010-08-02
Hi there, of course, also made me double check as I forgot to add an important part.

First I downloaded the correct drivers from [Realtek webpage]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8191SE-VA2")
Once downloaded, move to desktop and unzip on to desktop.
Next open a terminal and type in 
> sudo sufollowed by your administrator password
next type in
> cd <where driver is stored> do this by drag and dropping the unzipped driver file.
Next follow these commands
> make clean
> make
> make install
> modprobe 8192se_pci
> exit
You should now have a working wireless card
To change your router setting you will need the ip address and an ethernet cable connection, this should be supplied by isp or router manufacturer. Once you are connected just change your settings to open, bearing in mind that anyone can then see your router, so you may want to set is hidden as well.

Next, make sure it works after a restart, if not you will have to reinstall and follow the following steps:
> try adding r8192se_pci to /etc/modules

     Code:
     gksudo gedit /etc/modules 

                                                                              

---

### Post by Deut316 on 2010-08-30
Hi. what is the name of the driver file mentioned below.... what extension would it have?

> **mett demon said:**
> Hi there, of course, also made me double check as I forgot to add an important part.

First I downloaded the correct drivers from [Realtek webpage]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8191SE-VA2")
Once downloaded, move to desktop and unzip on to desktop.
Next open a terminal and type in 
followed by your administrator password
next type in
 do this by drag and dropping the unzipped driver file.
Next follow these commands





You should now have a working wireless card
To change your router setting you will need the ip address and an ethernet cable connection, this should be supplied by isp or router manufacturer. Once you are connected just change your settings to open, bearing in mind that anyone can then see your router, so you may want to set is hidden as well.

Next, make sure it works after a restart, if not you will have to reinstall and follow the following steps:

---

