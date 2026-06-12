---
title: "Upgrading to 0.23 broke Mythtv"
date: 2010-03-02
forum: Mythbuntu
---

### Post by zaurus on 2010-03-02
Hello

I activated 0.23 wekkly builds and cannot start either frontend or backend-setup. Only real mode is working. Any help please.

The second issue I have now is that my 3 DVB cards changes the device number after each reboot. How can I prevent that?

Thanks.

---

### Post by tgm4883 on 2010-03-02
What is "real mode"? Were you prompted to upgrade your DB? Any error messages? Log files?

---

### Post by geekyhawkes on 2010-03-02
SLightly off topic but is there a list anywhere as to what is new in .23?  I have asked google but not really found anything new listed.

---

### Post by zaurus on 2010-03-02
> **tgm4883 said:**
> What is "real mode"? Were you prompted to upgrade your DB? Any error messages? Log files?

Real mode: mythbackend-setup.real, mythfrontend.real. Yes, I was promted to upgrade my DB and I did it. As for log please advise where to get them /var/log/myth*?

KR

---

### Post by TheMiz on 2010-03-02
I didn't think 0.23 was released yet.

The main mythtv page ([http://www.mythtv.org/](http://www.mythtv.org/)) says its still just 0.22.

---

### Post by superm1 on 2010-03-02
Depending on the build you are running, there may be a bug with a bunch of shell scripts not being executable.

chmod a+x /usr/share/mythtv/*.sh should fix it.

Can you please verify your build and OS thought?

lsb_release -a
apt-cache policy mythtv-backend

---

### Post by tgm4883 on 2010-03-02
> **zaurus said:**
> Real mode: mythbackend-setup.real, mythfrontend.real. Yes, I was promted to upgrade my DB and I did it. As for log please advise where to get them /var/log/myth*?

KR

I had some trouble with that as well until I rebooted.


> **TheMiz said:**
> I didn't think 0.23 was released yet.

The main mythtv page ([http://www.mythtv.org/](http://www.mythtv.org/)) says its still just 0.22.

It's not. That doesn't mean that you can't upgrade to it though.

---

### Post by nickrout on 2010-03-02
Yes but 0.23 is trunk=experimental=try at your risk. It changes regularly and on some days it will simply be broken. Such is the nature of running svn software.

Do NOT run trunk unless you are subscribed to and READ the mythtv-dev mailing list. If you do, you aren't likely to be ready for it or to get much help.

---

### Post by tgm4883 on 2010-03-03
> **nickrout said:**
> Yes but 0.23 is trunk=experimental=try at your risk. It changes regularly and on some days it will simply be broken. Such is the nature of running svn software.

Do NOT run trunk unless you are subscribed to and READ the mythtv-dev mailing list. If you do, you aren't likely to be ready for it or to get much help.

Geez, you make it sound so bad to run something that is shipping for 10.04. Try to be constructive and help out here.

---

### Post by azmyth on 2010-03-03
> **geekyhawkes said:**
> SLightly off topic but is there a list anywhere as to what is new in .23?  I have asked google but not really found anything new listed.
There's a little bit of info here.
[http://www.mythtv.org/wiki/Release_Notes_-_0.23](http://www.mythtv.org/wiki/Release_Notes_-_0.23)

---

### Post by nickrout on 2010-03-03
> **tgm4883 said:**
> Geez, you make it sound so bad to run something that is shipping for 10.04. Try to be constructive and help out here.

Sorry you know better than the myth devs? This is the standard advice for running trunk.

---

### Post by zaurus on 2010-03-03
> **superm1 said:**
> Depending on the build you are running, there may be a bug with a bunch of shell scripts not being executable.

chmod a+x /usr/share/mythtv/*.sh should fix it.

Can you please verify your build and OS thought?

lsb_release -a
apt-cache policy mythtv-backend

chmod a+x /usr/share/mythtv/*.sh fixed it. Thanks a lot!

lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.10
Release:        9.10
Codename:       karmic

apt-cache policy mythtv-backend
mythtv-backend:
  Installed: 0.23.0~trunk23612-0ubuntu0~mythbuntu1
  Candidate: 0.23.0~trunk23612-0ubuntu0~mythbuntu1
  Version table:
 *** 0.23.0~trunk23612-0ubuntu0~mythbuntu1 0
        500 [http://uk.autobuilds.mythbuntu.org](http://uk.autobuilds.mythbuntu.org) karmic/main Packages
        100 /var/lib/dpkg/status
     0.22.0+fixes22594-0ubuntu1 0
        500 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) karmic/multiverse Packages
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/multiverse Packages
KR

A comment however. It is not that easy for a normal user to manage Mythtv.

---

### Post by zaurus on 2010-03-03
What about this?

The second issue I have now is that my 3 DVB cards changes the device number after each reboot. How can I prevent that?

Thanks.

---

### Post by joshoekstra on 2010-03-03
> **zaurus said:**
> What about this?

The second issue I have now is that my 3 DVB cards changes the device number after each reboot. How can I prevent that?

Thanks.

Search for: writing UDEV-rule, with the different how-to's out there you should be able to do it.

---

### Post by mymythtv on 2010-03-03
...or just write a **/etc/modprobe.d/my-card.conf** file...

> options cx23885 adapter_nr=0,1
options dvb-bt8xx adapter_nr=2

Or to get different load order

> options cx23885 adapter_nr=0
options dvb-bt8xx adapter_nr=1,2

Substitute names and numbers depending on hardware...

---

### Post by Neon Dusk on 2010-03-03
> **zaurus said:**
> What about this?

The second issue I have now is that my 3 DVB cards changes the device number after each reboot. How can I prevent that?

Thanks.

Check [thread=1311795]Force order of allocation of DVB frontends[/thread]

In some cases you may still need to create a udev rule - [thread=1334173]dvb card order[/thread]

---

### Post by zaurus on 2010-03-03
Thanks a lot everybody!Your inputs were very helpful.

---

### Post by tgm4883 on 2010-03-03
> **nickrout said:**
> Sorry you know better than the myth devs? This is the standard advice for running trunk.

Are you saying that the Mythbuntu-repos package should require you to subscribe to the mailing list before you can activate the 0.23 builds?

---

### Post by zaurus on 2010-03-03
> **mymythtv said:**
> ...or just write a **/etc/modprobe.d/my-card.conf** file...



Or to get different load order



Substitute names and numbers depending on hardware...

Sorry, why do you specify two numbers 0,1 for cx23885 and 
only one 2 for dvb-bt8xx?

And what string from this output should I use in the file my-card.conf?

0: Philips TDA10023 DVB-C
1: Afatech AF9013 DVB-T
2: Conexant CX24116/CX24118

root@lanbox:~# dmesg | grep dvb
[   16.104910] dvb-usb: found a 'Afatech AF9015 DVB-T USB2.0 stick' in warm state.
[   16.104955] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   16.931624] cx88/2: cx2388x dvb driver version 0.0.7 loaded
[   16.931628] cx88/2: registering cx8802 driver, type: dvb access: shared
[   17.153514] dvb-usb: Afatech AF9015 DVB-T USB2.0 stick successfully initialized and connected.
[   17.159303] usbcore: registered new interface driver dvb_usb_af9015
[   33.514324] cx24116_firmware_ondemand: Waiting for firmware upload (dvb-fe-cx24116.fw)...
[   33.514332] cx88_audio 0000:03:07.1: firmware: requesting dvb-fe-cx24116.fw
root@lanbox:~#

---

### Post by Neon Dusk on 2010-03-03
I think your drivers would be

budget_av
dvb_usb_af9015
cx88_dvb

If the card was a dual tuner you would give two values for the adapter_nr parameter.

---

### Post by zaurus on 2010-03-05
I am still struggling with DVB-card´s order. None of the methods above work for me. No idea why.
I fixed quite easy my remote with udev-rules for inputs. But DVBs a bit harder to fix. Any further advise?

---

### Post by nickrout on 2010-03-05
> **tgm4883 said:**
> Are you saying that the Mythbuntu-repos package should require you to subscribe to the mailing list before you can activate the 0.23 builds?

I am saying that the mythtv devs recommend that if you run trunk you (1) should be prepared for beakages (2) you should subscribe to the dev list to keep up with the state of development.

---

### Post by Neon Dusk on 2010-03-05
> **zaurus said:**
> I am still struggling with DVB-card´s order. None of the methods above work for me. No idea why.
I fixed quite easy my remote with udev-rules for inputs. But DVBs a bit harder to fix. Any further advise?

Creating a modprobe conf file and setting the adapter_nr parameter should be the easiest solution.

Can you post what you tried and the output of lsmod?

---

### Post by zaurus on 2010-03-06
> **Neon Dusk said:**
> Creating a modprobe conf file and setting the adapter_nr parameter should be the easiest solution.

Can you post what you tried and the output of lsmod?

This is the last one
# To Identify serial nos etc for a Device use
# udevadm info -a -p $(udevadm info -q path -n /dev/dvb/adapter0/frontend0)
#
# Creates an adapter100 link for the Nova card & adapter101 link for the Twinhan card

# Terratec C-1200 DVB-C
# SUBSYSTEM=="dvb",KERNELS=="0000:03:06.0",DRIVERS=="budget_av",SYMLINK+="terratec"


# Hauppage HVR-4000 DVB-S/S2/T
# SUBSYSTEM=="dvb",KERNELS=="0000:03:07.2",DRIVERS=="cx88-mpeg driver manager",SYMLINK+="hauppage"

# Roxcore - DVB-T
SUBSYSTEM=="dvb",ATTRS{idVendor}=="15a4",ATTRS{idProduct}=="9016",ATTRS{manufacturer}=="Afatech",ATTRS{product}=="DVB-T",SYMLINK="roxcore"

lsmod | grep dvb
cx88_dvb               24356  11
cx88_vp3054_i2c         3136  1 cx88_dvb
videobuf_dvb            8452  1 cx88_dvb
cx8802                 17956  1 cx88_dvb
cx88xx                 86412  4 cx88_dvb,cx8802,cx88_alsa,cx8800
videobuf_dma_sg        14436  7 bttv,cx88_dvb,saa7146_vv,cx8802,cx88_alsa,cx8800,cx88xx
videobuf_core          21188  7 bttv,videobuf_dvb,saa7146_vv,cx8802,cx8800,cx88xx,videobuf_dma_sg
dvb_usb_af9015         32964  1
dvb_usb                19276  1 dvb_usb_af9015
dvb_core              104528  5 cx88_dvb,videobuf_dvb,budget_av,budget_core,dvb_usb

0: Afatech AF9013 DVB-T
1: Philips TDA10023 DVB-C
2: Conexant CX24116/CX24118

This setup seems to work because I have the same order now for several hot/cold boot. But I need Afatech as card num 3, because sometimes I use it om another PC.

As I said I tried also your original udev setup and modprobe.conf setup without result. Here the configs for both:

10-local.rules (not workng)
# Terratec C-1200 DVB-C
SUBSYSTEM=="dvb", KERNELS=="0000:03:06.0", DRIVERS=="budget_av", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter0/%%s $${K#*.}'", SYMLINK+="%c"


#Hauppage HVR-4000 DVB-S/S2/T
SUBSYSTEM=="dvb", KERNELS=="0000:03:07.2", DRIVERS=="cx88-mpeg driver manager", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter1/%%s $${K#*.}'", SYMLINK+="%c"

#Roxcore - DVB-T
SUBSYSTEM=="dvb", ATTRS{idVendor}=="15a4", ATTRS{idProduct}=="9016", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter2/%%s $${K#*.}'", SYMLINK+="%c"

my-card.conf (not working)

# options TDA10023 adapter_nr=0
# options CX24116/CX24118 adapter_nr=1
# options AF9013 adapter_nr=2
option budget_av adapter_nr=0
option dvb_usb_af9015 adapter_nr=3
option cx88_dvb adapter_nr=1,2

---

### Post by Neon Dusk on 2010-03-06
The udev rules don't change the adapter order they just create a consistent symlink that you can then use in MythTv

> **zaurus said:**
> 
...
SUBSYSTEM=="dvb",KERNELS=="0000:03:06.0",DRIVERS=="budget_av",SYMLINK+="terratec"
...


Don't think this will work and if it did would create a symlink called 'terratec' for your Terratec card. Do you see the terratec symlink when you do a 'ls  /dev/dvb/'?

> **zaurus said:**
> 
...I need Afatech as card num 3, because sometimes I use it om another PC.


?? If you have consistent adapter numbers or symlinks then the card order shouldn't matter.

> **zaurus said:**
> 
10-local.rules (not workng)
# Terratec C-1200 DVB-C
SUBSYSTEM=="dvb", KERNELS=="0000:03:06.0", DRIVERS=="budget_av", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter0/%%s $${K#*.}'", SYMLINK+="%c"


This isn't working as you've changed it from adapter100 to adapter0 so it's going to fail when it attempts to create a symlink with the same name as an existing device

> **zaurus said:**
> 
my-card.conf (not working)

# options TDA10023 adapter_nr=0
# options CX24116/CX24118 adapter_nr=1
# options AF9013 adapter_nr=2
option budget_av adapter_nr=0
option dvb_usb_af9015 adapter_nr=3
option cx88_dvb adapter_nr=1,2

It should be option**s** and I think the HVR 4000 (cx88_dvb) only creates 1 adapter

---

### Post by zaurus on 2010-03-06
Thanks Neon Dusk!

How to modify your script to adapt to my needs i.e. 100 -> 0, 101 -> 1 etc?

How do I check if symlinks are really created? In mythbackend setup I still see dvb numbers instead of names! Though with the latest check dvb order was changed again but mythbackend assigned right cards with new order.

---

### Post by Neon Dusk on 2010-03-06
As I said before it's probably easier to use the modprobe options. So disable your udev rules and my-card.conf file. Create /etc/modprobe.d/options-dvb.conf

```

#Terratec C-1200 DVB-C options
options budget_av adapter_nr=4

#Hauppage HVR-4000 DVB-S/S2/T
options cx88_dvb adapter_nr=5

#Roxcore - DVB-T
options dvb_usb_af9015 adapter_nr=6

```

Reboot and confirm with 

```

ls /dev/dvb/

```

That you see adapters 4,5,6 listed. If this works you can change the adapter_nr values e.g.
```


#Terratec C-1200 DVB-C options
options budget_av adapter_nr=0

#Hauppage HVR-4000 DVB-S/S2/T
options cx88_dvb adapter_nr=1

#Roxcore - DVB-T
options dvb_usb_af9015 adapter_nr=2

```

If you're going the udev route then

/etc/udev/rules.d/10-local.rules

```

# Terratec C-1200 DVB-C
SUBSYSTEM=="dvb", KERNELS=="0000:03:06.0", DRIVERS=="budget_av", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter100/%%s $${K#*.}'", SYMLINK+="%c"


#Hauppage HVR-4000 DVB-S/S2/T
SUBSYSTEM=="dvb", KERNELS=="0000:03:07.2", DRIVERS=="cx88-mpeg driver manager", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter101/%%s $${K#*.}'", SYMLINK+="%c"

#Roxcore - DVB-T
SUBSYSTEM=="dvb", ATTRS{idVendor}=="15a4", ATTRS{idProduct}=="9016", PROGRAM="/bin/sh -c 'K=%k; K=$${K#dvb}; printf dvb/adapter102/%%s $${K#*.}'", SYMLINK+="%c"

```

Reboot and confirm the adapter100, adapter101, adapter102 symlinks have been created
```

ls /dev/dvb/

```

In MythTv you should then be able to select adapter100, adapter101, adapter102 (adapter0,adapter1,adapter2 will still be listed but you should use the new symlinks instead)

---

### Post by Mrazek on 2010-04-28
Back to 0.23 :-)
Zaurus, please, are you able to send any info how you upgraded to 0.23? I have Mythbuntu 9.10 with 0.22 and have problems in frontend when switching between DVB-T and analog stations (black screen) and want to try if it's fixed in 0.23.

---

