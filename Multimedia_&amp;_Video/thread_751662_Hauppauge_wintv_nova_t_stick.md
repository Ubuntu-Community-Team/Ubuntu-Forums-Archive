---
title: "Hauppauge wintv nova t stick"
date: 2008-04-10
forum: Multimedia &amp; Video
---

### Post by dan888 on 2008-04-10
Hi,

I bought the following device earlier today after reading others had got it to work... I cant get it to work under either 7.10 gutsy or 8.04 hardy.

The box label underneath says wintv-nova-t-stick model 1185 G SL-1185-v2.0-uk

In fact here it is;

[http://www.currys.co.uk/martprd/store/cur_page.jsp?BV_SessionID=@@@@0506684713.1207868039@@@@&BV_EngineID=ccciadedkhhkffkcflgceggdhhmdgmi.0&page=Product&fm=null&sm=null&tm=null&sku=226218&category_oid=](http://www.currys.co.uk/martprd/store/cur_page.jsp?BV_SessionID=@@@@0506684713.1207868039@@@@&BV_EngineID=ccciadedkhhkffkcflgceggdhhmdgmi.0&page=Product&fm=null&sm=null&tm=null&sku=226218&category_oid=)

So when I plug it in I get;

tail /var/log/messages
Apr 10 23:51:02 server03 kernel: [ 3620.018878] usb 4-2.1: new high speed USB device using ehci_hcd and address 10
Apr 10 23:51:02 server03 kernel: [ 3620.111832] usb 4-2.1: configuration #1 chosen from 1 choice

I downloaded the following firmware and copied it to the /lib/firmware dir;
dvb-usb-nova-t-usb2-02.fw

still get the same as above in messages when i unplug and plug

help.

---

### Post by wolfen69 on 2008-04-10
see this [http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices#Hauppauge_WinTV-NOVA-T_usb2](http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices#Hauppauge_WinTV-NOVA-T_usb2)  it says you also need the following drivers:

- dib3000-common.ko
 - dib3000mc.ko
 - dvb-usb.ko
 - dvb-usb-dibusb-common.ko
 - dvb-usb-nova-t-usb2.ko

---

### Post by dan888 on 2008-04-11
Hi.

My device is a Hauppauge WinTV NovaT Stick rather than the older USB2 model (see picture in previous post)
Any other suggestions that could help?

I found this;
[http://article.gmane.org/gmane.linux.drivers.dvb/37772](http://article.gmane.org/gmane.linux.drivers.dvb/37772)

But have no idea how to go about it?

Dan

---

### Post by wolfen69 on 2008-04-11
it would appear that you should navigate to those directories and add what he wrote to a file.

---

### Post by dan888 on 2008-04-11
bash: cd: /linux/drivers/media/dvb/dvb-usb: No such file or directory

do those dir exist on ubuntu? if so where?

I cant find "dvb-usb-ids.h" anywhere on my system
whats the best way to search from cmd?

also tried;

user01@server04:/$ sudo find -iname 'dvb_*.h'
find: ./home/user01/.gvfs: Permission denied
./usr/src/linux-headers-2.6.24-16/drivers/media/dvb/dvb-core/dvb_filter.h
./usr/src/linux-headers-2.6.24-16/drivers/media/dvb/dvb-core/dvb_math.h
./usr/src/linux-headers-2.6.24-16/drivers/media/dvb/dvb-core/dvb_demux.h
./usr/src/linux-headers-2.6.24-16/drivers/media/dvb/dvb-core/dvb_ringbuffer.h
./usr/src/linux-headers-2.6.24-16/drivers/media/dvb/dvb-core/dvb_frontend.h
./usr/src/linux-headers-2.6.24-16/drivers/media/dvb/dvb-core/dvb_ca_en50221.h
./usr/src/linux-headers-2.6.24-16/drivers/media/dvb/dvb-core/dvb_net.h
./usr/src/linux-headers-2.6.24-16/drivers/media/dvb/frontends/dvb_dummy_fe.h


but dont have the file? help?

---

### Post by anthonyJC on 2008-04-12
he user downloaded the kernel source and placed it in a folder called linux.  BTW he must of been on an older kernel because that file isn't there anymore. I couldn't find the replacement, there is nothing like that id file in the hardy kernel. Also the kernel 2.6.24-15 of hardy doesn't include the addition of the nova sticks, freeze was on 2.6.24-16. Also be aware you would have to compile modules to apply the patch (I don't know if you know this or not.) best thing is to sit and wait until a kernel update for it to be supported. you might want to move to fedora for this since they are always updating to the latest kernel, on a weekly basis.

---

### Post by dan888 on 2008-04-12
that sounds fairly hardcore!!!, should i switch to a diff card?

---

### Post by anthonyJC on 2008-04-12
i've just done a search and someone has already done the work necessary here : [http://ubuntuforums.org/showthread.php?t=533528](http://ubuntuforums.org/showthread.php?t=533528)

---

### Post by xc3RnbFO8P on 2008-04-12
I got this usb stik and I use this instruction:
[http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers]("http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers")
And I use:
make all
make install

Here is my "sudo find -iname 'dvb_*.h')
```
./v4l-dvb/v4l/dvb_demux.h
./v4l-dvb/v4l/dvb_ringbuffer.h
./v4l-dvb/v4l/dvb_filter.h
./v4l-dvb/v4l/dvb_dummy_fe.h
./v4l-dvb/v4l/dvb_frontend.h
./v4l-dvb/v4l/dvb_ca_en50221.h
./v4l-dvb/v4l/dvb_math.h
./v4l-dvb/v4l/dvb_net.h
./v4l-dvb/linux/drivers/media/dvb/dvb-core/dvb_demux.h
./v4l-dvb/linux/drivers/media/dvb/dvb-core/dvb_ringbuffer.h
./v4l-dvb/linux/drivers/media/dvb/dvb-core/dvb_filter.h
./v4l-dvb/linux/drivers/media/dvb/dvb-core/dvb_frontend.h
./v4l-dvb/linux/drivers/media/dvb/dvb-core/dvb_ca_en50221.h
./v4l-dvb/linux/drivers/media/dvb/dvb-core/dvb_math.h
./v4l-dvb/linux/drivers/media/dvb/dvb-core/dvb_net.h
./v4l-dvb/linux/drivers/media/dvb/frontends/dvb_dummy_fe.h
rob@rob-desktop:~$ 

```

---

### Post by dan888 on 2008-04-12
I've tried that;
his first instruction is to plug in the stick and do;
dmesg

he gets;
[ 5828.308000] dvb-usb: found a 'Hauppauge Nova-T Stick' in cold state, will try to load a firmware
[ 5828.412000] dvb-usb: did not find the firmware file. (dvb-usb-dib0700-01.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2) 

i get;
[33865.091066] usb 7-3: new high speed USB device using ehci_hcd and address 7
[33865.223954] usb 7-3: configuration #1 chosen from 1 choice

Fallen at the first hirdle!

---

### Post by anthonyJC on 2008-04-12
maybe because hardy is long term release they took nova-t stick support out because it was unfinished work? Here's someone else with the same problem [http://ubuntuforums.org/showthread.php?t=702870](http://ubuntuforums.org/showthread.php?t=702870), and here's someone who tried to compile a module (bit it's for feisty-so it's old) [http://ubuntuforums.org/showthread.php?t=37588](http://ubuntuforums.org/showthread.php?t=37588)

---

### Post by dan888 on 2008-04-15
> **Ringi said:**
> I got this usb stik and I use this instruction:
[http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers]("http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers")
And I use:
make all
make install

Here is my "sudo find -iname 'dvb_*.h')
```
./v4l-dvb/v4l/dvb_demux.h
./v4l-dvb/v4l/dvb_ringbuffer.h
./v4l-dvb/v4l/dvb_filter.h
./v4l-dvb/v4l/dvb_dummy_fe.h
./v4l-dvb/v4l/dvb_frontend.h
./v4l-dvb/v4l/dvb_ca_en50221.h
./v4l-dvb/v4l/dvb_math.h
./v4l-dvb/v4l/dvb_net.h
./v4l-dvb/linux/drivers/media/dvb/dvb-core/dvb_demux.h
./v4l-dvb/linux/drivers/media/dvb/dvb-core/dvb_ringbuffer.h
./v4l-dvb/linux/drivers/media/dvb/dvb-core/dvb_filter.h
./v4l-dvb/linux/drivers/media/dvb/dvb-core/dvb_frontend.h
./v4l-dvb/linux/drivers/media/dvb/dvb-core/dvb_ca_en50221.h
./v4l-dvb/linux/drivers/media/dvb/dvb-core/dvb_math.h
./v4l-dvb/linux/drivers/media/dvb/dvb-core/dvb_net.h
./v4l-dvb/linux/drivers/media/dvb/frontends/dvb_dummy_fe.h
rob@rob-desktop:~$ 

```

That worked a treat! Thanks for that...
Dan

---

