---
title: "Build failed V4L-DVB Device Drivers"
date: 2015-02-27
forum: Multimedia Software
---

### Post by Tuyen_Nguyen on 2015-02-27
Hi,
I am following the instructions here: [http://www.linuxtv.org/wiki/index.ph...Device_Drivers]("http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers")

Specifically:
```
git clone git://linuxtv.org/media_build.git
cd media_build
./build
```
I get the following failure:
```
Checking if the needed tools for Ubuntu 14.04.1 LTS are available
Needed package dependencies are met.

************************************************************
* This script will download the latest tarball and build it*
* Assuming that your kernel is compatible with the latest  *
* drivers. If not, you'll need to add some extra backports,*
* ./backports/<kernel> directory.                          *
* It will also update this tree to be sure that all compat *
* bits are there, to avoid compilation failures            *
************************************************************
************************************************************
* All drivers and build system are under GPLv2 License     *
* Firmware files are under the license terms found at:     *
* http://www.linuxtv.org/downloads/firmware/               *
* Please abort in the next 5 secs if you don't agree with  *
* the license                                              *
************************************************************

Not aborted. It means that the licence was agreed. Proceeding...

****************************
Updating the building system
****************************
From git://linuxtv.org/media_build
 * branch            master     -> FETCH_HEAD
Already up-to-date.
make: Entering directory `/home/tuyennguyen/media_build/linux'
wget http://linuxtv.org/downloads/drivers/linux-media-LATEST.tar.bz2.md5 -O linux-media.tar.bz2.md5.tmp
--2015-02-27 16:15:59--  http://linuxtv.org/downloads/drivers/linux-media-LATEST.tar.bz2.md5
Resolving linuxtv.org (linuxtv.org)... 130.149.80.248
Connecting to linuxtv.org (linuxtv.org)|130.149.80.248|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 101 [application/x-bzip2]
Saving to: ‘linux-media.tar.bz2.md5.tmp’

100%[==================================================================================>] 101         --.-K/s   in 0s      

2015-02-27 16:16:00 (7,44 MB/s) - ‘linux-media.tar.bz2.md5.tmp’ saved [101/101]

cat: linux-media.tar.bz2.md5: No such file or directory
--2015-02-27 16:16:00--  http://linuxtv.org/downloads/drivers/linux-media-LATEST.tar.bz2
Resolving linuxtv.org (linuxtv.org)... 130.149.80.248
Connecting to linuxtv.org (linuxtv.org)|130.149.80.248|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5084200 (4,8M) [application/x-bzip2]
Saving to: ‘linux-media.tar.bz2’

100%[==================================================================================>] 5.084.200   18,1KB/s   in 3m 9s  

2015-02-27 16:19:10 (26,2 KB/s) - ‘linux-media.tar.bz2’ saved [5084200/5084200]

make: Leaving directory `/home/tuyennguyen/media_build/linux'
make: Entering directory `/home/tuyennguyen/media_build/linux'
tar xfj linux-media.tar.bz2
rm -f .patches_applied .linked_dir .git_log.md5
make: Leaving directory `/home/tuyennguyen/media_build/linux'
**********************************************************
* Downloading firmwares from linuxtv.org.                *
**********************************************************
as102_data1_st.hex
as102_data2_st.hex
cmmb_vega_12mhz.inp
cmmb_venice_12mhz.inp
dvb-fe-bcm3510-01.fw
dvb-fe-drxj-mc-1.0.8.fw
dvb-fe-drxj-mc-vsb-1.0.8.fw
dvb-fe-drxj-mc-vsb-qam-1.0.8.fw
dvb-fe-or51132-qam.fw
dvb-fe-or51132-vsb.fw
dvb-fe-or51211.fw
dvb-fe-xc4000-1.4.1.fw
dvb-fe-xc5000-1.6.114.fw
dvb-fe-xc5000c-4.1.30.7.fw
dvb-firmwares.tar.bz2
dvb-ttpci-01.fw-261a
dvb-ttpci-01.fw-261b
dvb-ttpci-01.fw-261c
dvb-ttpci-01.fw-261d
dvb-ttpci-01.fw-261f
dvb-ttpci-01.fw-2622
dvb-usb-avertv-a800-02.fw
dvb-usb-bluebird-01.fw
dvb-usb-dib0700-1.20.fw
dvb-usb-dibusb-5.0.0.11.fw
dvb-usb-dibusb-6.0.0.8.fw
dvb-usb-dtt200u-01.fw
dvb-usb-it9135-01.fw
dvb-usb-it9135-02.fw
dvb-usb-terratec-h5-drxk.fw
dvb-usb-terratec-h7-az6007.fw
dvb-usb-terratec-h7-drxk.fw
dvb-usb-umt-010-02.fw
dvb-usb-vp702x-01.fw
dvb-usb-vp7045-01.fw
dvb-usb-wt220u-01.fw
dvb-usb-wt220u-02.fw
dvb_nova_12mhz.inp
dvb_nova_12mhz_b0.inp
isdbt_nova_12mhz.inp
isdbt_nova_12mhz_b0.inp
isdbt_rio.inp
sms1xxx-hcw-55xxx-dvbt-02.fw
sms1xxx-hcw-55xxx-isdbt-02.fw
sms1xxx-nova-a-dvbt-01.fw
sms1xxx-nova-b-dvbt-01.fw
sms1xxx-stellar-dvbt-01.fw
tdmb_nova_12mhz.inp
v4l-cx231xx-avcore-01.fw
v4l-cx23418-apu.fw
v4l-cx23418-cpu.fw
v4l-cx23418-dig.fw
v4l-cx23885-avcore-01.fw
v4l-cx23885-enc-broken.fw
v4l-cx25840.fw
******************
* Start building *
******************
make -C /home/tuyennguyen/media_build/v4l allyesconfig
make[1]: Entering directory `/home/tuyennguyen/media_build/v4l'
make[2]: Entering directory `/home/tuyennguyen/media_build/linux'
Applying patches for kernel 3.13.0-45-generic
patch -s -f -N -p1 -i ../backports/api_version.patch
patch -s -f -N -p1 -i ../backports/pr_fmt.patch
1 out of 1 hunk FAILED
make[2]: *** [apply_patches] Error 1
make[2]: Leaving directory `/home/tuyennguyen/media_build/linux'
make[1]: *** [allyesconfig] Error 2
make[1]: Leaving directory `/home/tuyennguyen/media_build/v4l'
make: *** [allyesconfig] Error 2
can't select all drivers at ./build line 490.
```

Thank for any help!

---

### Post by Bucky Ball on 2015-02-27
Welcome. What device are you using? If it is USB, please open a terminal with it plugged in and give the output of:

```
lsusb
```

---

### Post by Tuyen_Nguyen on 2015-02-27
Hi! 
Thank for reply! Here is my device:
```
tuyennguyen@TuyenNguyen:~$ lsusb
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 005: ID 0bda:0139 Realtek Semiconductor Corp. RTS5139 Card Reader Controller
Bus 002 Device 004: ID 04f2:b40a Chicony Electronics Co., Ltd 
Bus 002 Device 006: ID 0e8d:763f MediaTek Inc. 
Bus 002 Device 002: ID 1a81:1705 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


```

---

