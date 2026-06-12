---
title: "Freecom DVB-T USB Stick Revision 4 (RTL2831U chipset)"
date: 2008-01-12
forum: Multimedia &amp; Video
---

### Post by ugm6hr on 2008-01-12
I've just made the mistake of getting a Freecom DVB-T USB Stick.

Unfortunately, while Revisions 1-3 work with firmware, this current revision does not.

I found this post, which offers some hope: [http://article.gmane.org/gmane.linux.drivers.dvb/37634indicate](http://article.gmane.org/gmane.linux.drivers.dvb/37634indicate)

Details of the chipset:
[http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PNid=22&PFid=35&Level=4&Conn=3&ProdID=147](http://www.realtek.com.tw/products/productsView.aspx?Langid=1&PNid=22&PFid=35&Level=4&Conn=3&ProdID=147)

LinuxTV:
[http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices#Freecom_rev_4_DVB-T_USB_2.0_tuner](http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices#Freecom_rev_4_DVB-T_USB_2.0_tuner)

Anyone actually managed to use this in Linux / Ubuntu?

lsusb:
```
Bus 003 Device 002: ID 14aa:0160 AVerMedia (again) or C&E 

```

---

### Post by xc3RnbFO8P on 2008-01-12
Do you have dvb-usb-wt220u-fc03.fw in your computer?

If not look at this:  [http://www.ryanlothian.com/articles/v4l-dvb]("http://www.ryanlothian.com/articles/v4l-dvb")

---

### Post by ugm6hr on 2008-01-12
> **Ringi said:**
> Do you have dvb-usb-wt220u-fc03.fw in your computer?

If not look at this:  [http://www.ryanlothian.com/articles/v4l-dvb]("http://www.ryanlothian.com/articles/v4l-dvb")

No - haven't tried that yet.

My concern was that the new Revision 4 stick is completely different than the previous versions....

That site does not give an lsusb output for me to compare my stick with.

If no one has any other ideas - might give it a try anyway.

---

### Post by ugm6hr on 2008-01-19
This is looking less hopeful:
[http://www.hantslug.org.uk/lurker/message/20071207.191118.c664fabb.en.html](http://www.hantslug.org.uk/lurker/message/20071207.191118.c664fabb.en.html)

Other statements: [http://forum.freecompromo.com/viewtopic.php?p=9186&sid=7b0b97cd039ad50ccfcbd83a41481ea1](http://forum.freecompromo.com/viewtopic.php?p=9186&sid=7b0b97cd039ad50ccfcbd83a41481ea1)

---

### Post by ugm6hr on 2008-01-20
I realise it is just me in my own thread now!

Surely there must be other people out there with this device?

This offered me a bit of hope, if it is real.....
[http://youtube.com/watch?v=wmUMFRyylgE](http://youtube.com/watch?v=wmUMFRyylgE)

A DVB-T based on the same chipset working with the EEE PC, in what looks like the standard Xandros-based OS.

EDIT: A reply from the video poster states that this was a modified EEE with PCLinuxOS - but that it is genuine.  So it must be possible!

---

### Post by tiwag on 2008-01-22
Hello ugm6hr

i'm looking forward too in order to get my Freecom DVBT (RTL2831U) USB running soon...

brgds tiwag

---

### Post by tiwag on 2008-01-23
i asked Realtek if they have any linux driver for their RTL2831U chipset,
and they sent me the following package, which can be downloaded here

[http://tiwag.cb.googlepages.com/rtl2831u_dvb-usb_v0.0.1.tar.gz](http://tiwag.cb.googlepages.com/rtl2831u_dvb-usb_v0.0.1.tar.gz)   (92kB)

***********************************************************************************************
Dear Customer,

Thank you for your E-mail. Attached is RTL2831U Linux driver for Kernel 2.6.22

Best Regards!

Technical Support Dept.
Realtek Semiconductor  Corp.

***********************************************************************************************

but i don't know how to build this with ubuntu

if someone knows how to build, please respond here

thanks & brgds
tiwag

---

### Post by ugm6hr on 2008-01-23
I have given this a try, but have hit a brick wall...

This is what I have doe so far (following readme):
> $ cp usr/src/linux-headers-2.6.22-14/drivers/media/dvb/dvb-usb ~/dvb-usb

Uncompress driver

Copy all files to linux kernel 2.6.21.4 source code in usr/src/linux-headers-2.6.22-14/drivers/media/dvb/dvb-usb

Add the following lines to Makefile in dvb-usb or you can refereence ex_Makefile.

dvb-usb-rtl2831u-objs = math_mpi.o foundation.o demod_rtl2830.o tuner_demod_io.o tuner_mxl5005s.o mt_spuravoid.o \

	mt_userdef.o mt2060_basic.o tuner.o MT2060Tuner.o rtd2830.o rtd2830u.o

obj-$(CONFIG_DVB_USB_RTL2831U) += dvb-usb-rtl2831u.o



Add the following lines to Kconfig in dvb-usb or you can refereence ex_Kconfig.	

config DVB_USB_RTL2831U

	tristate "Realtek RTL2831U DVB-T USB2.0 support"

	depends on DVB_USB

	help

	  Realtek RTL2831U DVB-T driver.

$ sudo apt-get install libncurses5-dev kernel-package gcc-3.3

$ cd /usr/src/linux-headers-2.6.22-14-generic/

$ sudo make menuconfig

Use arrow keys to navigate, Enter to select submenu and Y to choose options (mark with * or M to activate as below):
		Device Drivers  --->

			Multimedia devices  ---> 

				[*] DVB For Linux 

				[*]   Load and attach frontend modules as needed

				[*]   DVB/ATSC adapters --->

					<M>   Support for various USB DVB devices

					.......

					<M>   Realtek RTL2831U DVB-T USB2.0 support (new)

Exit (multiple times) and select Yes to save kernel config on final exit

Not sure if all those extra packages are necessary.  But despite adding lots more, I am stuck on the next command:
[http://ubuntuforums.org/showthread.php?t=675929](http://ubuntuforums.org/showthread.php?t=675929)

---

### Post by ugm6hr on 2008-01-26
I have progressed with compiling a bit now...

Hopefully will return with a complete how-to...

Progress so far: [http://ubuntuforums.org/showthread.php?p=4192548#post4192548](http://ubuntuforums.org/showthread.php?p=4192548#post4192548)

---

### Post by ugm6hr on 2008-01-27
OK. Tried this at a location with excellent signal.

Kaffeine does not pick up any channels on scanning.

dmesg output:
```
[ 6069.864000] - rtd2830_set_parameters
[ 6070.048000] rtd2830_read_snr: ***snr =0*** 
[ 6070.052000]   rtd2830_read_status ******FSM = 0******
[ 6070.052000]   rtd2830_read_status ******FSM = 0******
[ 6070.056000]   rtd2830_read_status ******FSM = 0******
[ 6070.056000] + rtd2830_set_parameters
[ 6070.056000] rtd2830_read_signal_strength: signal strength =0 
[ 6070.064000] rtd2830_read_snr: ***snr =0*** 
[ 6070.064000]   rtd2830_read_status ******FSM = 0******
[ 6070.064000] + rtd2830_set_parameters
[ 6070.332000] +rtd2830_soft_reset
[ 6070.340000] -rtd2830_soft_reset
[ 6071.576000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6071.764000] +rtd2830_soft_reset
[ 6071.768000] -rtd2830_soft_reset
[ 6072.916000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6073.104000] +rtd2830_soft_reset
[ 6073.108000] -rtd2830_soft_reset
[ 6074.256000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6074.256000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6074.416000] - rtd2830_set_parameters
[ 6074.600000]   rtd2830_read_status ******FSM = 0******
[ 6074.600000]   rtd2830_read_status ******FSM = 0******
[ 6074.604000]   rtd2830_read_status ******FSM = 0******
[ 6074.604000] + rtd2830_set_parameters
[ 6074.608000] rtd2830_read_signal_strength: signal strength =0 
[ 6074.608000]   rtd2830_read_status ******FSM = 0******
[ 6074.608000] + rtd2830_set_parameters
[ 6074.876000] +rtd2830_soft_reset
[ 6074.884000] -rtd2830_soft_reset
[ 6076.120000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6076.308000] +rtd2830_soft_reset
[ 6076.316000] -rtd2830_soft_reset
[ 6077.460000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6077.644000] +rtd2830_soft_reset
[ 6077.652000] -rtd2830_soft_reset
[ 6078.800000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6078.800000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6078.960000] - rtd2830_set_parameters
[ 6079.144000] rtd2830_read_snr: ***snr =0*** 
[ 6079.148000]   rtd2830_read_status ******FSM = 0******
[ 6079.148000]   rtd2830_read_status ******FSM = 0******
[ 6079.152000]   rtd2830_read_status ******FSM = 0******
[ 6079.152000] + rtd2830_set_parameters
[ 6079.152000] rtd2830_read_signal_strength: signal strength =0 
[ 6079.156000]   rtd2830_read_status ******FSM = 0******
[ 6079.156000] + rtd2830_set_parameters
[ 6079.424000] +rtd2830_soft_reset
[ 6079.428000] -rtd2830_soft_reset
[ 6080.664000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6080.852000] +rtd2830_soft_reset
[ 6080.860000] -rtd2830_soft_reset
[ 6082.004000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6082.192000] +rtd2830_soft_reset
[ 6082.200000] -rtd2830_soft_reset
[ 6083.344000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6083.344000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6083.504000] - rtd2830_set_parameters
[ 6083.688000] rtd2830_read_snr: ***snr =0*** 
[ 6083.692000]   rtd2830_read_status ******FSM = 0******
[ 6083.692000]   rtd2830_read_status ******FSM = 0******
[ 6083.696000]   rtd2830_read_status ******FSM = 0******
[ 6083.696000] + rtd2830_set_parameters
[ 6083.696000] rtd2830_read_signal_strength: signal strength =0 
[ 6083.700000]   rtd2830_read_status ******FSM = 0******
[ 6083.700000] + rtd2830_set_parameters
[ 6083.968000] +rtd2830_soft_reset
[ 6083.976000] -rtd2830_soft_reset
[ 6085.212000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6085.400000] +rtd2830_soft_reset
[ 6085.404000] -rtd2830_soft_reset
[ 6086.552000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6086.740000] +rtd2830_soft_reset
[ 6086.744000] -rtd2830_soft_reset
[ 6087.892000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6087.892000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6088.048000] - rtd2830_set_parameters
[ 6088.232000] rtd2830_read_snr: ***snr =0*** 
[ 6088.232000]   rtd2830_read_status ******FSM = 0******
[ 6088.236000]   rtd2830_read_status ******FSM = 0******
[ 6088.236000]   rtd2830_read_status ******FSM = 0******
[ 6088.236000] + rtd2830_set_parameters
[ 6088.240000] rtd2830_read_signal_strength: signal strength =0 
[ 6088.240000]   rtd2830_read_status ******FSM = 0******
[ 6088.240000] + rtd2830_set_parameters
[ 6088.508000] +rtd2830_soft_reset
[ 6088.512000] -rtd2830_soft_reset
[ 6089.748000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6089.932000] +rtd2830_soft_reset
[ 6089.936000] -rtd2830_soft_reset
[ 6091.084000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6091.272000] +rtd2830_soft_reset
[ 6091.276000] -rtd2830_soft_reset
[ 6092.424000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6092.424000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6092.580000] - rtd2830_set_parameters
[ 6092.768000] rtd2830_read_snr: ***snr =0*** 
[ 6092.772000]   rtd2830_read_status ******FSM = 0******
[ 6092.772000]   rtd2830_read_status ******FSM = 0******
[ 6092.772000] + rtd2830_set_parameters
[ 6092.776000]   rtd2830_read_status ******FSM = 0******
[ 6092.776000]   rtd2830_read_status ******FSM = 0******
[ 6092.776000] + rtd2830_set_parameters
[ 6093.052000] +rtd2830_soft_reset
[ 6093.056000] -rtd2830_soft_reset
[ 6094.292000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6094.480000] +rtd2830_soft_reset
[ 6094.484000] -rtd2830_soft_reset
[ 6095.632000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6095.816000] +rtd2830_soft_reset
[ 6095.824000] -rtd2830_soft_reset
[ 6096.968000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6096.968000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6097.124000] - rtd2830_set_parameters
[ 6097.308000] rtd2830_read_signal_strength: signal strength =0 
[ 6097.316000] rtd2830_read_snr: ***snr =0*** 
[ 6097.320000]   rtd2830_read_status ******FSM = 0******
[ 6097.320000]   rtd2830_read_status ******FSM = 0******
[ 6097.320000] + rtd2830_set_parameters
[ 6097.324000]   rtd2830_read_status ******FSM = 0******
[ 6097.324000]   rtd2830_read_status ******FSM = 0******
[ 6097.324000] + rtd2830_set_parameters
[ 6097.588000] +rtd2830_soft_reset
[ 6097.596000] -rtd2830_soft_reset
[ 6098.832000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6099.016000] +rtd2830_soft_reset
[ 6099.024000] -rtd2830_soft_reset
[ 6100.168000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6100.352000] +rtd2830_soft_reset
[ 6100.360000] -rtd2830_soft_reset
[ 6101.504000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6101.504000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6101.660000] - rtd2830_set_parameters
[ 6101.840000] rtd2830_read_signal_strength: signal strength =0 
[ 6101.848000] rtd2830_read_snr: ***snr =0*** 
[ 6101.848000]   rtd2830_read_status ******FSM = 0******
[ 6101.852000]   rtd2830_read_status ******FSM = 0******
[ 6101.852000]   rtd2830_read_status ******FSM = 0******
[ 6101.852000] + rtd2830_set_parameters
[ 6101.856000] rtd2830_read_signal_strength: signal strength =0 
[ 6101.860000]   rtd2830_read_status ******FSM = 0******
[ 6101.860000] + rtd2830_set_parameters
[ 6102.128000] +rtd2830_soft_reset
[ 6102.136000] -rtd2830_soft_reset
[ 6103.372000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6103.560000] +rtd2830_soft_reset
[ 6103.568000] -rtd2830_soft_reset
[ 6104.712000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6104.896000] +rtd2830_soft_reset
[ 6104.904000] -rtd2830_soft_reset
[ 6106.048000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6106.048000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6106.204000] - rtd2830_set_parameters
[ 6106.392000] rtd2830_read_snr: ***snr =0*** 
[ 6106.392000]   rtd2830_read_status ******FSM = 0******
[ 6106.392000]   rtd2830_read_status ******FSM = 0******
[ 6106.396000]   rtd2830_read_status ******FSM = 0******
[ 6106.396000] + rtd2830_set_parameters
[ 6106.400000] rtd2830_read_signal_strength: signal strength =0 
[ 6106.400000]   rtd2830_read_status ******FSM = 0******
[ 6106.400000] + rtd2830_set_parameters
[ 6106.668000] +rtd2830_soft_reset
[ 6106.676000] -rtd2830_soft_reset
[ 6107.912000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6108.100000] +rtd2830_soft_reset
[ 6108.108000] -rtd2830_soft_reset
[ 6109.252000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6109.444000] +rtd2830_soft_reset
[ 6109.448000] -rtd2830_soft_reset
[ 6110.596000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6110.596000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6110.752000] - rtd2830_set_parameters
[ 6110.752000] rtd2830_get_tune_settings: Do Nothing
[ 6110.928000] + rtd2830_set_parameters
[ 6111.200000] +rtd2830_soft_reset
[ 6111.208000] -rtd2830_soft_reset
[ 6112.444000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6112.632000] +rtd2830_soft_reset
[ 6112.640000] -rtd2830_soft_reset
[ 6113.784000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6113.976000] +rtd2830_soft_reset
[ 6113.984000] -rtd2830_soft_reset
[ 6115.128000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6115.128000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6115.288000] - rtd2830_set_parameters
[ 6115.288000]   rtd2830_read_status ******FSM = 0******
[ 6115.288000] + rtd2830_set_parameters
[ 6115.548000] +rtd2830_soft_reset
[ 6115.556000] -rtd2830_soft_reset
[ 6116.792000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6116.980000] +rtd2830_soft_reset
[ 6116.988000] -rtd2830_soft_reset
[ 6118.132000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6118.320000] +rtd2830_soft_reset
[ 6118.328000] -rtd2830_soft_reset
[ 6119.472000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6119.472000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6119.632000] - rtd2830_set_parameters
[ 6119.820000] rtd2830_read_signal_strength: signal strength =0 
[ 6119.824000]   rtd2830_read_status ******FSM = 0******
[ 6119.824000]   rtd2830_read_status ******FSM = 0******
[ 6119.824000] + rtd2830_set_parameters
[ 6119.832000] rtd2830_read_snr: ***snr =0*** 
[ 6119.832000]   rtd2830_read_status ******FSM = 0******
[ 6119.832000] + rtd2830_set_parameters
[ 6120.096000] +rtd2830_soft_reset
[ 6120.104000] -rtd2830_soft_reset
[ 6121.340000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6121.524000] +rtd2830_soft_reset
[ 6121.532000] -rtd2830_soft_reset
[ 6122.676000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6122.864000] +rtd2830_soft_reset
[ 6122.872000] -rtd2830_soft_reset
[ 6124.016000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6124.016000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6124.176000] - rtd2830_set_parameters
[ 6124.356000]   rtd2830_read_status ******FSM = 0******
[ 6124.356000]   rtd2830_read_status ******FSM = 0******
[ 6124.360000]   rtd2830_read_status ******FSM = 0******
[ 6124.360000] + rtd2830_set_parameters
[ 6124.360000] rtd2830_read_signal_strength: signal strength =0 
[ 6124.368000] rtd2830_read_snr: ***snr =0*** 
[ 6124.372000]   rtd2830_read_status ******FSM = 0******
[ 6124.372000] + rtd2830_set_parameters
[ 6124.636000] +rtd2830_soft_reset
[ 6124.644000] -rtd2830_soft_reset
[ 6125.880000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6126.068000] +rtd2830_soft_reset
[ 6126.076000] -rtd2830_soft_reset
[ 6127.220000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6127.404000] +rtd2830_soft_reset
[ 6127.408000] -rtd2830_soft_reset
[ 6128.556000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6128.556000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6128.716000] - rtd2830_set_parameters
[ 6128.896000]   rtd2830_read_status ******FSM = 0******
[ 6128.904000]   rtd2830_read_status ******FSM = 0******
[ 6128.904000]   rtd2830_read_status ******FSM = 0******
[ 6128.904000] + rtd2830_set_parameters
[ 6128.908000] rtd2830_read_signal_strength: signal strength =0 
[ 6128.908000]   rtd2830_read_status ******FSM = 0******
[ 6128.908000] + rtd2830_set_parameters
[ 6129.184000] +rtd2830_soft_reset
[ 6129.188000] -rtd2830_soft_reset
[ 6130.436000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6130.624000] +rtd2830_soft_reset
[ 6130.632000] -rtd2830_soft_reset
[ 6131.776000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6131.964000] +rtd2830_soft_reset
[ 6131.968000] -rtd2830_soft_reset
[ 6133.116000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6133.116000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6133.276000] - rtd2830_set_parameters
[ 6133.468000] rtd2830_read_snr: ***snr =0*** 
[ 6133.468000]   rtd2830_read_status ******FSM = 0******
[ 6133.472000]   rtd2830_read_status ******FSM = 0******
[ 6133.472000]   rtd2830_read_status ******FSM = 0******
[ 6133.472000] + rtd2830_set_parameters
[ 6133.476000] rtd2830_read_signal_strength: signal strength =0 
[ 6133.476000]   rtd2830_read_status ******FSM = 0******
[ 6133.476000] + rtd2830_set_parameters
[ 6133.748000] +rtd2830_soft_reset
[ 6133.752000] -rtd2830_soft_reset
[ 6134.988000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6135.172000] +rtd2830_soft_reset
[ 6135.180000] -rtd2830_soft_reset
[ 6136.324000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6136.516000] +rtd2830_soft_reset
[ 6136.524000] -rtd2830_soft_reset
[ 6137.672000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6137.672000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6137.828000] - rtd2830_set_parameters
[ 6138.016000] rtd2830_read_snr: ***snr =0*** 
[ 6138.016000]   rtd2830_read_status ******FSM = 0******
[ 6138.020000]   rtd2830_read_status ******FSM = 0******
[ 6138.020000]   rtd2830_read_status ******FSM = 0******
[ 6138.020000] + rtd2830_set_parameters
[ 6138.024000] rtd2830_read_signal_strength: signal strength =0 
[ 6138.024000]   rtd2830_read_status ******FSM = 0******
[ 6138.024000] + rtd2830_set_parameters
[ 6138.292000] +rtd2830_soft_reset
[ 6138.300000] -rtd2830_soft_reset
[ 6139.536000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6139.720000] +rtd2830_soft_reset
[ 6139.728000] -rtd2830_soft_reset
[ 6140.872000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6141.064000] +rtd2830_soft_reset
[ 6141.068000] -rtd2830_soft_reset
[ 6142.216000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6142.216000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6142.376000] - rtd2830_set_parameters
[ 6142.564000] rtd2830_read_snr: ***snr =0*** 
[ 6142.564000]   rtd2830_read_status ******FSM = 0******
[ 6142.568000]   rtd2830_read_status ******FSM = 0******
[ 6142.568000]   rtd2830_read_status ******FSM = 0******
[ 6142.568000] + rtd2830_set_parameters
[ 6142.572000] rtd2830_read_signal_strength: signal strength =0 
[ 6142.576000]   rtd2830_read_status ******FSM = 0******
[ 6142.576000] + rtd2830_set_parameters
[ 6142.848000] +rtd2830_soft_reset
[ 6142.852000] -rtd2830_soft_reset
[ 6144.088000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6144.272000] +rtd2830_soft_reset
[ 6144.280000] -rtd2830_soft_reset
[ 6145.424000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6145.608000] +rtd2830_soft_reset
[ 6145.616000] -rtd2830_soft_reset
[ 6146.760000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6146.760000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6146.916000] - rtd2830_set_parameters
[ 6147.104000] rtd2830_read_snr: ***snr =0*** 
[ 6147.108000]   rtd2830_read_status ******FSM = 0******
[ 6147.108000]   rtd2830_read_status ******FSM = 0******
[ 6147.108000]   rtd2830_read_status ******FSM = 0******
[ 6147.108000] + rtd2830_set_parameters
[ 6147.112000] rtd2830_read_signal_strength: signal strength =0 
[ 6147.116000]   rtd2830_read_status ******FSM = 0******
[ 6147.116000] + rtd2830_set_parameters
[ 6147.388000] +rtd2830_soft_reset
[ 6147.392000] -rtd2830_soft_reset
[ 6148.628000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6148.820000] +rtd2830_soft_reset
[ 6148.828000] -rtd2830_soft_reset
[ 6149.972000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6150.160000] +rtd2830_soft_reset
[ 6150.168000] -rtd2830_soft_reset
[ 6151.312000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6151.312000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6151.464000] - rtd2830_set_parameters
[ 6151.656000] rtd2830_read_snr: ***snr =0*** 
[ 6151.656000]   rtd2830_read_status ******FSM = 0******
[ 6151.660000]   rtd2830_read_status ******FSM = 0******
[ 6151.660000]   rtd2830_read_status ******FSM = 0******
[ 6151.660000] + rtd2830_set_parameters
[ 6151.664000] rtd2830_read_signal_strength: signal strength =0 
[ 6151.668000]   rtd2830_read_status ******FSM = 0******
[ 6151.668000] + rtd2830_set_parameters
[ 6151.940000] +rtd2830_soft_reset
[ 6151.944000] -rtd2830_soft_reset
[ 6153.180000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6153.368000] +rtd2830_soft_reset
[ 6153.372000] -rtd2830_soft_reset
[ 6154.520000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6154.704000] +rtd2830_soft_reset
[ 6154.708000] -rtd2830_soft_reset
[ 6155.856000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6155.856000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6156.012000] - rtd2830_set_parameters
[ 6156.200000] rtd2830_read_snr: ***snr =0*** 
[ 6156.200000]   rtd2830_read_status ******FSM = 0******
[ 6156.204000]   rtd2830_read_status ******FSM = 0******
[ 6156.204000]   rtd2830_read_status ******FSM = 0******
[ 6156.204000] + rtd2830_set_parameters
[ 6156.208000]   rtd2830_read_status ******FSM = 0******
[ 6156.208000] + rtd2830_set_parameters
[ 6156.476000] +rtd2830_soft_reset
[ 6156.480000] -rtd2830_soft_reset
[ 6157.716000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6157.908000] +rtd2830_soft_reset
[ 6157.916000] -rtd2830_soft_reset
[ 6159.060000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6159.252000] +rtd2830_soft_reset
[ 6159.256000] -rtd2830_soft_reset
[ 6160.404000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6160.404000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6160.560000] - rtd2830_set_parameters
[ 6160.744000] rtd2830_read_signal_strength: signal strength =0 
[ 6160.752000] rtd2830_read_snr: ***snr =0*** 
[ 6160.752000]   rtd2830_read_status ******FSM = 0******
[ 6160.756000]   rtd2830_read_status ******FSM = 0******
[ 6160.756000]   rtd2830_read_status ******FSM = 0******
[ 6160.756000] + rtd2830_set_parameters
[ 6160.760000] rtd2830_read_signal_strength: signal strength =0 
[ 6160.760000]   rtd2830_read_status ******FSM = 0******
[ 6160.760000] + rtd2830_set_parameters
[ 6161.032000] +rtd2830_soft_reset
[ 6161.036000] -rtd2830_soft_reset
[ 6162.272000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6162.456000] +rtd2830_soft_reset
[ 6162.460000] -rtd2830_soft_reset
[ 6163.608000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6163.792000] +rtd2830_soft_reset
[ 6163.800000] -rtd2830_soft_reset
[ 6164.944000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6164.944000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6165.104000] - rtd2830_set_parameters
[ 6165.284000] rtd2830_read_snr: ***snr =0*** 
[ 6165.284000]   rtd2830_read_status ******FSM = 0******
[ 6165.288000]   rtd2830_read_status ******FSM = 0******
[ 6165.288000]   rtd2830_read_status ******FSM = 0******
[ 6165.288000] + rtd2830_set_parameters
[ 6165.292000] rtd2830_read_signal_strength: signal strength =0 
[ 6165.296000]   rtd2830_read_status ******FSM = 0******
[ 6165.296000] + rtd2830_set_parameters
[ 6165.568000] +rtd2830_soft_reset
[ 6165.576000] -rtd2830_soft_reset
[ 6166.812000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6167.004000] +rtd2830_soft_reset
[ 6167.012000] -rtd2830_soft_reset
[ 6168.156000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6168.344000] +rtd2830_soft_reset
[ 6168.352000] -rtd2830_soft_reset
[ 6169.496000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6169.496000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6169.652000] - rtd2830_set_parameters
[ 6169.836000] rtd2830_read_snr: ***snr =0*** 
[ 6169.836000]   rtd2830_read_status ******FSM = 0******
[ 6169.840000]   rtd2830_read_status ******FSM = 0******
[ 6169.840000]   rtd2830_read_status ******FSM = 0******
[ 6169.840000] + rtd2830_set_parameters
[ 6169.844000] rtd2830_read_signal_strength: signal strength =0 
[ 6169.844000]   rtd2830_read_status ******FSM = 0******
[ 6169.844000] + rtd2830_set_parameters
[ 6170.120000] +rtd2830_soft_reset
[ 6170.124000] -rtd2830_soft_reset
[ 6171.360000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6171.548000] +rtd2830_soft_reset
[ 6171.552000] -rtd2830_soft_reset
[ 6172.700000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6172.880000] +rtd2830_soft_reset
[ 6172.888000] -rtd2830_soft_reset
[ 6174.032000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6174.032000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6174.192000] - rtd2830_set_parameters
[ 6174.376000] rtd2830_read_snr: ***snr =0*** 
[ 6174.376000]   rtd2830_read_status ******FSM = 0******
[ 6174.380000]   rtd2830_read_status ******FSM = 0******
[ 6174.380000]   rtd2830_read_status ******FSM = 0******
[ 6174.380000] + rtd2830_set_parameters
[ 6174.384000] rtd2830_read_signal_strength: signal strength =0 
[ 6174.384000]   rtd2830_read_status ******FSM = 0******
[ 6174.384000] + rtd2830_set_parameters
[ 6174.652000] +rtd2830_soft_reset
[ 6174.660000] -rtd2830_soft_reset
[ 6175.896000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6176.084000] +rtd2830_soft_reset
[ 6176.088000] -rtd2830_soft_reset
[ 6177.236000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6177.424000] +rtd2830_soft_reset
[ 6177.428000] -rtd2830_soft_reset
[ 6178.576000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6178.576000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6178.732000] - rtd2830_set_parameters
[ 6178.916000] rtd2830_read_snr: ***snr =0*** 
[ 6178.916000]   rtd2830_read_status ******FSM = 0******
[ 6178.920000]   rtd2830_read_status ******FSM = 0******
[ 6178.920000]   rtd2830_read_status ******FSM = 0******
[ 6178.920000] + rtd2830_set_parameters
[ 6178.924000] rtd2830_read_signal_strength: signal strength =0 
[ 6178.928000]   rtd2830_read_status ******FSM = 0******
[ 6178.928000] + rtd2830_set_parameters
[ 6179.192000] +rtd2830_soft_reset
[ 6179.200000] -rtd2830_soft_reset
[ 6180.436000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6180.624000] +rtd2830_soft_reset
[ 6180.628000] -rtd2830_soft_reset
[ 6181.776000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6181.964000] +rtd2830_soft_reset
[ 6181.968000] -rtd2830_soft_reset
[ 6183.112000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6183.112000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6183.268000] - rtd2830_set_parameters
[ 6183.460000] rtd2830_read_snr: ***snr =0*** 
[ 6183.460000]   rtd2830_read_status ******FSM = 0******
[ 6183.460000]   rtd2830_read_status ******FSM = 0******
[ 6183.464000]   rtd2830_read_status ******FSM = 0******
[ 6183.464000] + rtd2830_set_parameters
[ 6183.468000] rtd2830_read_signal_strength: signal strength =0 
[ 6183.468000]   rtd2830_read_status ******FSM = 0******
[ 6183.468000] + rtd2830_set_parameters
[ 6183.728000] +rtd2830_soft_reset
[ 6183.736000] -rtd2830_soft_reset
[ 6184.972000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6185.160000] +rtd2830_soft_reset
[ 6185.168000] -rtd2830_soft_reset
[ 6186.312000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6186.500000] +rtd2830_soft_reset
[ 6186.508000] -rtd2830_soft_reset
[ 6187.652000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6187.652000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6187.812000] - rtd2830_set_parameters
[ 6187.992000]   rtd2830_read_status ******FSM = 0******
[ 6187.992000] + rtd2830_set_parameters
[ 6187.996000]   rtd2830_read_status ******FSM = 0******
[ 6187.996000] + rtd2830_set_parameters
[ 6188.264000] +rtd2830_soft_reset
[ 6188.272000] -rtd2830_soft_reset
[ 6189.508000] rtd2830_scan_channel_procedure : FsmStage < 5 
[ 6189.700000] +rtd2830_soft_reset
[ 6189.704000] -rtd2830_soft_reset
[ 6190.852000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6191.040000] +rtd2830_soft_reset
[ 6191.048000] -rtd2830_soft_reset
[ 6192.192000] rtd2830_scan_channel_procedure : *****TPS_NON_LOCK***** 
[ 6192.192000] rtd2830_scan_channel_procedure : ***** Signal NOT Present***** 
[ 6192.348000] - rtd2830_set_parameters
[ 6192.348000] rtd2830_sleep: Do Nothing

```

So it seems to be doing something, but it doesn't work :confused:

---

### Post by ftonti on 2008-01-31
any progress so far? Thanks for trying!

Cheers, Fabio

---

### Post by ugm6hr on 2008-01-31
> **ftonti said:**
> any progress so far? Thanks for trying!

Cheers, Fabio

Nothing since my last post.

I'm not sure what the problem is...

The driver loads OK, the DVB-T stick appears to be working, but it doesn't pick up any channels.

I'm stumped!

There are a few people trying to resolve this on the dvb mailing list - they've got no further than me though :(

---

### Post by Andy_NL on 2008-02-05
Hi,

I've manages to compile this driver aswell and get is loaded.

'dmesg | grep dvb' gives

dvb-usb: found a 'Freecom USB 2.0 DVB-T Device' in warm state.
dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
dvb-usb: schedule remote query interval to 300 msecs.
dvb-usb: Freecom USB 2.0 DVB-T Device successfully initialized and connected.
usbcore: registered new interface driver dvb_usb_rtd2831u

My question is: what to do next. How do i get this device active?

Thanks,
Andy

---

### Post by ugm6hr on 2008-02-05
Andy

Seems you've got a more promising dmesg than me!

Have you tried just using Kaffeine to see whether it will pick up channels?  I think there are command-line ways to check whether it works - but I don't understand them well enough.

---

### Post by Andy_NL on 2008-02-06
Yes, but no channels are found.
I'm not sure I'm scanning the correct frequencies.
My dmesg has alot of messages like you posted earlier.
Seems like my device has the same problem.

---

### Post by stealthbanana on 2008-02-18
I have the same chipset in my DVB USB thingy. An Azurwave DT200U USBID ID 13d3:3216

I have taken the drivers and done a makefile, added a few kernel headers needed so it is compilable and insertable without having to compile the whole kernel.  If you want this, PM me.  Working on making a debianised package for module assistant (not made a deb for years so it will take time).

Anyway, here is the output of dmesg

```

[ 6145.184000] usb 4-2: USB disconnect, address 3
[ 6151.096000] usb 4-2: new high speed USB device using ehci_hcd and address 4
[ 6151.228000] usb 4-2: configuration #1 chosen from 1 choice
[ 6151.296000] dvb-usb: found a 'DTV-DVB UDTT 7047-USB 2.0 DVB-T Driver' in warm state.
[ 6151.296000] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 6151.296000] DVB: registering new adapter (DTV-DVB UDTT 7047-USB 2.0 DVB-T Driver).
[ 6151.296000] +rtd2831u_fe_attach
[ 6151.296000] -rtd2831u_fe_attach
[ 6151.296000] DVB: registering frontend 0 (Realtek RTD2830 DVB-T)...
[ 6151.300000] input: IR-receiver inside an USB DVB receiver as /class/input/input7
[ 6151.300000] dvb-usb: schedule remote query interval to 300 msecs.
[ 6151.300000] dvb-usb: DTV-DVB UDTT 7047-USB 2.0 DVB-T Driver successfully initialized and connected.
[ 6151.300000] usbcore: registered new interface driver dvb_usb_rtd2831u


```

Anyway, thats the output of dmesg.  Now I need to go make an 8m cable so I can actually get a signal to it

---

### Post by ugm6hr on 2008-02-18
So does this work?

Sounds good that you don't have to recompile the whole kernel, but I couldn't get it to work even after recompiling.

If it does work, I'd certainly appreciate the file and a How-to...

---

### Post by tiwag on 2008-02-19
> **stealthbanana said:**
> I have the same chipset in my DVB USB thingy. An Azurwave DT200U USBID ID 13d3:3216

I have taken the drivers and done a makefile, added a few kernel headers needed so it is compilable and insertable without having to compile the whole kernel.  If you want this...

for sure we want this ! :)

you could post a How-to here or in a new thread please.

thanks tiwag

---

### Post by stealthbanana on 2008-02-19
OK, got it working and watching telly on it now, I think it actually works better on Linux than it does on Windows.  OK This method is not very nice, but it works, and that's what counts.

Download the repackaged source from here, feel free to mirror it so my ISP doesn't shout at me

[http://coronach.adsl24.co.uk/code/rtl2831u_dvb-usb_v0.0.1.tar.bz2](http://coronach.adsl24.co.uk/code/rtl2831u_dvb-usb_v0.0.1.tar.bz2)

I have written a readmeubuntu.txt file in the Doc directory, here is the contents.
_______________
Changes for Ubuntu Gutsy.

19-02-2008

Quck and dirty hack.

The source as supplied requires recompilation of the kernel from source.   

Added Makefile to compile as add on module.

Source references several kernel source files.  These were added in to the directory.  The following files were taken from the kernel source.

demux.h
dmxdev.h
dvb_demux.h
dvbdev.h
dvb_frontend.h
dvb_net.h
dvb-pll.h
dvb_ringbuffer.h
dvbt_demod_base.h
dvb-usb.h
dvb-usb-ids.h

Kernel version (uname -a)
Linux 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

 If doing this for other kernels, add these files.


Installing.

You will need the build-essential package and the kernel headers installed

Unpack the archive somewhere you like.

cd to the directory

type the following commands

make
sudo make install

It will throw up a few warnings, just ignore these for the moment.  I will try and fix them at a later date.

plug in your tuner, check dmesg that it has been seen and check the modules using:

lsmod | grep dvb

you should see something like:

```

dvb_usb_rtl2831u       91396  8
dvb_usb                21644  1 dvb_usb_rtl2831u
dvb_core               82216  1 dvb_usb
dvb_pll                15492  1 dvb_usb
i2c_core               26112  3 dvb_usb,dvb_pll,i2c_piix4
usbcore               138632  6 ndiswrapper,dvb_usb_rtl2831u,dvb_usb,ehci_hcd,ohci_hcd

```
And thats it.

I have checked using Kaffeine on two separate computers, works a treat, to cut down on channel scan time, select your transmitter, else an auto scan will take ages.

Use of this is at your own risk.  Its a dirty way, but it works for me.   
_________________

very simple.  

I would be interested in any feedback and if it works for you.  I did have one problem in that only a few channels were been found, but changing the lead from the aerial socket fixed all that.

---

### Post by ugm6hr on 2008-02-19
Thanks for this.

I will try and give it a go some time in the next week.  My reception where I am at the moment is pretty poor - so I won't be able to tell if it a reception issue or driver.

PS: I have uploaded the file to: 
[http://www.mediafire.com/?41g2zdizymt](http://www.mediafire.com/?41g2zdizymt)

---

### Post by sempronius on 2008-02-19
Hey, great news!!

Unfortunately, I am bit confused by the exact procedure needed to get things working...


1) Do I still have to follow the instructions in the original rtl2831u_dvb-usb_v0.0.1.tar.gz (not your repackaged one), as one can read in Doc/readme.txt?
So do I still have to copy all the files in your repackaged version (those that also exist in the original archive) to drivers/media/dvb/dvb-usb (the same files as in the original archive) or do I even have to copy _all_ the files in your new repackaged version?

2) Do I also have to do this (as described in readme.txt)?

        Step b. add the following lines to Makefile in dvb-usb or you can refereence ex_Makefile.
dvb-usb-rtl2831u-objs = math_mpi.o foundation.o demod_rtl2830.o tuner_demod_io.o tuner_mxl5005s.o m
t_spuravoid.o \
        mt_userdef.o mt2060_basic.o tuner.o MT2060Tuner.o rtd2830.o rtd2830u.o
obj-$(CONFIG_DVB_USB_RTL2831U) += dvb-usb-rtl2831u.o

        Step c. add the following lines to Kconfig in dvb-usb or you can refereence ex_Kconfig.
config DVB_USB_RTL2831U
        tristate "Realtek RTL2831U DVB-T USB2.0 support"
        depends on DVB_USB
        help
          Realtek RTL2831U DVB-T driver.


I guess, I still have to make these changes, right?


3) In your repackaged version you have a file Readmeubuntu.txt.

It talks about:

demux.h
dmxdev.h
dvb_demux.h
dvbdev.h
dvb_frontend.h
dvb_net.h
dvb-pll.h
dvb_ringbuffer.h
dvbt_demod_base.h
dvb-usb.h
dvb-usb-ids.h

Do these files ALSO have to be copied somewhere to the kernel source tree, or do they just stay in your repackaged version?

For example, I noticed that in my kernel source tree (and it is a 2.6.23 kernel), I have two instances of dvb-pll.h!?
One is in /drivers/media/dvb/frontends/,
the other in /drivers/media/dvb/dvb-core/

So if the above header files need to be copied, WHERE do they have to be copied (to both places)? 



Above all, I do not understand your statement:
"If doing this for other kernels, add these files."

Where to add? Asked again, add to the kernel source tree? (two both places, if a file exists in two directories)


Sorry if all this sounds silly. But so far I have not been lucky to find any channels. But maybe your hopefully NEW instructions will help me understand what exactly has to be done.


thanks so much

sempronius

---

### Post by stealthbanana on 2008-02-19
Very simple.

Install the kernel headers and build essentials

unpack the tar.bz2 file to a directory of your choice.

cd to the upacked directory

type

make

ignore the errors.then type

sudo make install

and thats it.

just do the tests to make sure it works and then watch TV.

---

### Post by sempronius on 2008-02-20
If I leave the kernel source alone (not copying any files from rtl2831u_dvb-usb_v0.0.1 there, not modifying Makefile and Kconfig in drivers/media/dvb/dvb-usb), no module dvb-pll can be selected in the kernel config (because tuner pll cannot be clicked on).

But dvb-pll is in your loaded modules.

Did you really leave the kernel source alone? (which means: not following the instructions in readme.txt in rtl2831u_dvb-usb_v0.0.1)

So far no luck...


sempronius

---

### Post by stealthbanana on 2008-02-20
I do not have the kernel source installed at all.  My aim was to create a stand alone installation for the module that did not require a full kernel recompilation, and so make it a very very simple process.

I copied the files listed from a copy of  the kernel source into the module directory so they could be used as the module depends upon them.  I listed them in case anyone was using a different kernel or different distro and needed to alter it for their system.

You just need the headers and build-essential (and I assume module-init-tools)

All you need to do on a standard ubuntu installation is unpack, and then make and sudo make install.

I am using kubuntu and kaffeine to watch at the moment.

You do not need to muck about with any kernel source, just 2 commands.

---

### Post by stealthbanana on 2008-02-20
Quick note.

This will not work with certain USB chips.  It depends on the tuner within the device.

The tuner in my device is an MXL5005, whereas the Freecom unit uses a MT2060 which is causing the problem.

I have an azurewave TU200 usb dongle.  but the same main chipset. 

Looks like freecom units are still a no go.

---

### Post by sempronius on 2008-02-20
> **stealthbanana said:**
> Quick note.

This will not work with certain USB chips.  It depends on the tuner within the device.

The tuner in my device is an MXL5005, whereas the Freecom unit uses a MT2060 which is causing the problem.

I have an azurewave TU200 usb dongle.  but the same main chipset. 

Looks like freecom units are still a no go.


Bummer.

Already suspected something like that (have been compiling like crazy and though your module was always made, no channels were found).

But thanks for this new information. So sadly, freecom users will have to be patient for some more time. :-(


sempronius

---

### Post by tiwag on 2008-02-20
[B][FONT="Arial Black"][SIZE="4"]good news for FREECOM DVB-T users
[/SIZE][/FONT][/B]
here is the working package

[http://tiwag.cb.googlepages.com/rtl2831u_dvb-usb_v0.0.2mod.tar.gz](http://tiwag.cb.googlepages.com/rtl2831u_dvb-usb_v0.0.2mod.tar.gz)

* extract the package to any folder where you have writing rights 
(a subfolder in your home folder e.g.)

* open a terminal window and type the commands
```
$ make
$ sudo make install

```

* install and start kaffeine and enjoy ...


[B]credits and thanks to stealthbanana and realtek
[/B]

brgds, tiwag

---

### Post by sempronius on 2008-02-20
Absolutely phantastic! For the first time in months my Freecom stick now also works under Linux.

And it was as easily as compiling the code during about two minutes.

I had one problem (virtual consoles and log files being flooded with messages), I got rid of it by simply removing all instances of printk. ;-)


thank you very much

sempronius

---

### Post by ftonti on 2008-02-21
GREAT!!! I'll try this very evening!

Just one more question:
> I had one problem (virtual consoles and log files being flooded with messages), I got rid of it by simply removing all instances of printk. 
What do you mean by that exactly?

Cheers, Fabio

---

### Post by sempronius on 2008-02-21
Well, the driver spits out huge amounts of messages to my various text consoles and also to my system log files. This way the log files grow to ridiculous sizes when watching TV for longer periods of time. Moreover - as I already wrote - my text consoles get flooded and cannot be used for different purposes during that time.

Of course, this also depends on my system log settings and how much I normally like to have logged and what kind of messages/errors etc.

And also:
All these messages are good, if you have a new driver and want to test it and check where there might be problems.


But since everything works very well, I do no longer need or want all these messages in my log files and on my text consoles, that's why I just removed all the instances of printk in the source code of the driver and compiled and installed the module again - now I get close to zero such messages.


sempronius


P.S.
Now if kaffeine only offered teletext, too.
I tried alevt, but only to find out it doesn't work with dvb-t. After a while, I found that I could patch alevt and get teletext, but in spite of its geometry option, the teletext window remains tiny and cannot be resized (preferably to a full screen teletext window).

Does anyone know a good teletext program for Linux?

---

### Post by ftonti on 2008-02-22
I just wanted to say that it works like a charm!!! 
Thanks everyone!

Anyway, I don't know about the Teletext stuff...

Cheers, Fabio

---

### Post by ftonti on 2008-02-22
I just wanted to say that it works like a charm!!! 
Thanks everyone!

Anyway, I don't know about the Teletext stuff...

Cheers, Fabio

---

### Post by sempronius on 2008-02-22
I am still excited by the fact that the stick now works with Linux.

In the meantime, however, I became aware of something that has me worried (a bit):

The stick gets considerably warmer under Linux than when I use it under Windows XP. In XP, it only gets warm when reception is poor, but when reception quality is good or when I do not use my TV program (don't watch TV), the stick stays cool or cools down again.

Not so in Linux, as soon as kaffeine has been started once, the green light of the stick stays on, even after shutting kaffeine down. Removing the driver modules doesn't change this either: The light stays on, and the stick gets very warm.

I am unsure whether this is of any major importance, though.


sempronius

---

### Post by juergi on 2008-02-24
First of all: Thanks to everyone for the great work. Now I can watch TV under Linux with the stick that I bought cause it  was said that it works with Linux (unfortunately I got the new one with Realtek-Chipset).

I can confirm:
- that it works better under Linux than under Windows (no stuttering)
- that the LED stays on and the stick get warm (but not hot) under Linux even when I don't watch TV and even when the computer is in standby mode

The last point results in a higher energy consumption which is a little bit annoying cause my master-slave power socket keeps voltage on all other devices.

One last question: Does anybody know, whether the IRDA-Device is accessible?

--- juergen

---

### Post by ugm6hr on 2008-02-24
This works great!  TV on my laptop, finally.

[http://ubuntuforums.org/showthread.php?p=4371178#post4371178](http://ubuntuforums.org/showthread.php?p=4371178#post4371178)

Just in case someone else gets the "no plugin for xxx.ts" error - just install the package libxine1-plugins in Synaptic Package manager.  It should then work.

---

### Post by coney on 2008-02-28
Hi,

sounds like everyone seems to now get the FREECOM (RTL2831U)  problemlessly running.

Doesn't seem to be doing that for me. 

I'm using a  **2.6.23** kernel and Gutsy Gibbon on a Toshiba Satellite A210-15Y notebook with an AMD64 X2.

Installed **rtl2831u_dvb-usb_v0.0.2mod** and it seems to be causing an*** oops***.

dmesg reads:

[  345.572913] dvb-usb: found a 'Freecom USB 2.0 DVB-T Device' in warm state.
[  345.572931] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[  345.575284] DVB: registering new adapter (Freecom USB 2.0 DVB-T Device)
[  345.575711]**[COLOR="Red"] Unable to handle kernel NULL pointer dereference at 0000000000000000[/COLOR]** RIP: 
[  345.575716]  [<ffffffff8841d74e>] :[COLOR="Blue"]dvb_usb_rtl2831u:rtd2831u_frontend_attach[/COLOR]+0xe/0x40
[  345.575732] PGD 75b2067 PUD 7568067 PMD 0 
[  345.575735] **[COLOR="Red"]Oops[/COLOR]**: 0002 [1] SMP 
[  345.575739] CPU 0 
[  345.575740] Modules linked in: dvb_usb_rtl2831u (...)

Could someone who has the stick running neatly compare his dmesg readings?

Thanx

Coney

---

### Post by coney on 2008-02-29
Hi. 

Sorry. Disregard previous Bulls***. I hadn't RTFM-ed. 

After reading the docs it dawned on me that the headerfiles that came with the [COLOR="Blue"]rtl2831u_dvb-usb_v0.0.2mod[/COLOR]  package where taken from the **2.6.21.4**  kernel so compiling against them naturally would cause errors since my kernel is a **2.6.23**. 

After copying

demux.h
dmxdev.h
dvb_demux.h
dvbdev.h
dvb_frontend.h
dvb_net.h
dvb-pll.h
dvb_ringbuffer.h
[COLOR="Red"]dvbt_demod_base.h[/COLOR] <---- this was nowhere in the kernel tree!!!
dvb-usb.h
dvb-usb-ids.h

from the kernel tree to the dircetory the [COLOR="Blue"]rtl2831u_dvb-usb_v0.0.2mod[/COLOR]  package was unpacked into and recompiling it worked as fine as everybody had said.

Great. Thanx!

Coney

---

### Post by ftonti on 2008-03-02
Thanks for all the help, everyone.

I just have one more question: how did you get the source distributed by freecom to compile as a module in the first place? Could someone maybe make a "how-to get a kernel driver to work as a module"? That would be a great reference! Or could you maybe just point me to some documentation?

I'm just trying to make it work with Sidux, and as I as far as I understand it, it seems that I need to get the necessary kernel headers from the 2.6.24 kernel? Is this right?

Thanks in advance, Fabio

---

### Post by ftonti on 2008-03-02
ok sorry my fault, didn't read the docs...

Thanks again, Fabio

---

### Post by MichaelSM on 2008-03-18
I think I'm out of my depth here. As usual.

I've followed instructions. Here's the main (?) results:


After dmesg ....(I've deleted some stuff to save space re. other apps.)

[   62.586691] dvb-usb: found a 'RTL2831U DVB-T USB2.0 DEVICE' in warm state.
[   62.586719] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   62.586975] DVB: registering new adapter (RTL2831U DVB-T USB2.0 DEVICE).
[   62.587963] BUG: unable to handle kernel NULL pointer dereference at virtual address 00000000
[   62.587979]  printing eip:
[   62.587982] f8d6dd1b
[   62.587985] *pde = 00000000
[   62.587993] Oops: 0002 [#1]
[   62.587995] SMP 
[   62.588002] Modules linked in: snd_seq_dummy snd_seq_oss dvb_usb_rtl2831u dvb_usb pcspkr dvb_core snd_seq_midi dvb_pll psmouse parport_pc parport serio_raw snd_emu10k1_synth snd_emux_synth snd_seq_virmidi snd_seq_midi_event snd_seq_midi_emul snd_emu10k1 snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss xpad snd_usb_audio snd_usb_lib snd_seq speedtch usbatm usblp snd_rawmidi snd_pcm snd_seq_device snd_timer snd_page_alloc snd_util_mem snd_hwdep i2c_viapro via_ircc irda nvidia(P) i2c_core via_agp agpgart emu10k1_gp gameport snd soundcore crc_ccitt shpchp pci_hotplug af_packet evdev tsdev ext3 jbd mbcache ide_cd cdrom ide_disk ata_generic libata scsi_mod usbhid hid via82cxxx floppy via_rhine mii generic uhci_hcd ehci_hcd ohci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor vesafb capability commoncap
[   62.588117] CPU:    0
[   62.588119] EIP:    0060:[<f8d6dd1b>]    Tainted: P      VLI
[   62.588120] EFLAGS: 00010282   (2.6.20-16-generic #2)
[   62.588142] EIP is at rtd2831u_frontend_attach+0xb/0x30 [dvb_usb_rtl2831u]
[   62.588147] eax: 00000000   ebx: dfd8680c   ecx: 00000000   edx: f8d6dd10
[   62.588151] esi: 00000000   edi: dfd86848   ebp: dfd86800   esp: f79b1da0
[   62.588155] ds: 007b   es: 007b   ss: 0068
[   62.588160] Process modprobe (pid: 3658, ti=f79b0000 task=c1b62a90 task.ti=f79b0000)
[   62.588163] Stack: dfd8680c f8c04f43 dfd8680c 00000000 dfd86848 dfd8680c f8c04754 f8c06090 
[   62.588175]        f8d6fcca f7d3d000 dfd86030 f8d73a80 f7d32c00 dfd86000 f8d72f70 00000000 
[   62.588186]        00000000 f8d72f70 00000000 f7d32c00 f7d32c00 f8d73920 f8d72dc0 f8d6da7c 
[   62.588197] Call Trace:
[   62.588208]  [<f8c04f43>] dvb_usb_adapter_frontend_init+0x13/0x100 [dvb_usb]
[   62.588242]  [<f8c04754>] dvb_usb_device_init+0x304/0x570 [dvb_usb]
[   62.588316]  [<f8d6da7c>] rtd2831u_usb_probe+0x1c/0x50 [dvb_usb_rtl2831u]
[   62.588343]  [<f887fc86>] usb_probe_interface+0x96/0xe0 [usbcore]
[   62.588415]  [<c0257c06>] really_probe+0x66/0x190
[   62.588439]  [<c0257d79>] driver_probe_device+0x49/0xc0
[   62.588475]  [<c0257f4e>] __driver_attach+0x9e/0xa0
[   62.588494]  [<c02570db>] bus_for_each_dev+0x3b/0x60
[   62.588529]  [<c0257aa4>] driver_attach+0x24/0x30
[   62.588536]  [<c0257eb0>] __driver_attach+0x0/0xa0
[   62.588542]  [<c025746b>] bus_add_driver+0x7b/0x1a0
[   62.588583]  [<f887f72b>] usb_register_driver+0x7b/0x100 [usbcore]
[   62.588639]  [<f8866013>] rtd2831u_usb_module_init+0x13/0x30 [dvb_usb_rtl2831u]
[   62.588663]  [<c014424d>] sys_init_module+0x15d/0x1ba0
[   62.588857]  [<c0107a8d>] sys_mmap2+0xcd/0xd0
[   62.588899]  [<c01031f0>] sysenter_past_esp+0x69/0xa9
[   62.588942]  [<c02e0033>] xfrm_state_find+0x283/0x570
[   62.588983]  =======================

michael@michael-desktop:~$ 


then,

michael@michael-desktop:~$ lsmod | grep dvb
dvb_usb_rtl2831u       90292  1 
dvb_usb                21644  1 dvb_usb_rtl2831u
dvb_core               80808  1 dvb_usb
dvb_pll                15364  1 dvb_usb
i2c_core               22656  5 i2c_ec,dvb_usb,dvb_pll,i2c_viapro,nvidia
usbcore               134280  13 dvb_usb_rtl2831u,dvb_usb,xpad,snd_usb_audio,snd_usb_lib,speedtch,usbatm,usblp,usbhid,uhci_hcd,ehci_hcd,ohci_hcd
michael@michael-desktop:~$ 


I've enabled DVB client in Kaffeine.

lsusb hangs in terminal with no output with the stick plugged in. I have to reboot with the stick unplugged to get a lsusb outcome.

I'm Feisty kernel 2.6.20 etc.

If it's a kernel issue am I in trouble?

Thanks in advance.

Mike.

PS. I've re-read Coney's posts but got lost in translation. If someone could explain it I'd be rapt!

---

### Post by stealthbanana on 2008-03-18
> **MichaelSM said:**
> I think I'm out of my depth here. As usual.

I've followed instructions. Here's the main (?) results:


After dmesg ....(I've deleted some stuff to save space re. other apps.)

<snip>

I'm Feisty kernel 2.6.20 etc.

If it's a kernel issue am I in trouble?

Thanks in advance.

Mike.

PS. I've re-read Coney's posts but got lost in translation. If someone could explain it I'd be rapt!

How did you compile the module?  If you read the readme file, it states it is only for Gutsy (kernel 2.6.22).  You will have to change various modules in the source to work on your specific kernel.  This method detailed in the readme.

The drivers should be in the mainline kernel about version 2.6.27 as it needs some further clean up and testing.

---

### Post by MichaelSM on 2008-03-18
Thank you, Stealtbanana.

I was right about being out of my depth.

I didn't check out the read-me docs at all. I enabled 'execute file as program' in Permissions, I extracted the directory to Desktop. In Terminal I typed cd (space) then dragged the directory into Terminal then at the prompt typed 'make', then after a short wait; at the next prompt I entered sudo make install + pw and so on.

'It' obviously didn't work, because I never got back to michael@michael-desktop:~$

So it IS a kernel issue. What's kernel 2.6.27?

I'm not a programmer as you can tell.

Sorry if I'm wasting your time.

Mike.

PS I've e-mailed Realtek asking for a tar package to suit my earlier kernel, if that helps.

---

### Post by stealthbanana on 2008-03-18
2.6.27 will be a future release of the linux kernel, I suspect it, or a later one, will be shipped with ubuntu 8.10 ( in the future).  I can tell the future, I am a prophet :P

I do not have a feisty installation here, but you will need to grab the sources of the kernel, copy and paste the required files to the source folder, overwriting those already there and then make. I am not sure if it will even compile on your kernel as they were released by realtek written for kernel 2.6.22.  As I stated this was a nasty hack but it worked, and work is going on to get them into the main Linux kernel.  

I would urge you to update your system if you want to use your DVB card, though it may be better waiting until hardy is released.  Updating the drivers in this hack for hardy will no doubt be done very quickly by some enterprising chap or chapette and posted here.

As for realtek, they just released the source for the drivers and using their method requires a full recompilation of the kernel and some in depth hacking, my aim was just to get a simple way for them to work.  If you are patient they will work soon if you update your installation.

---

### Post by MichaelSM on 2008-03-20
Thanks again Stealthbanana.

I returned the dvb-t usb unit to the retailer for a full refund. Too many dramas.

Your advice greatly appreciated.

Mike.

---

### Post by coney on 2008-03-25
Hi Mike,

you probably already solved the problem, since you posted 6 days ago.

Your problem is obvious: You have a kernel **[COLOR="Red"][COLOR="Red"]2.6.20[/COLOR][/COLOR]** while the headerfiles that come with the driver and reside in the directory the driver tarball unpacks into - "[COLOR="Plum"]rtl2831u_dvb-usb_v0.0.2mod[/COLOR]" in my case and most likely the same in yours - are taken from a**[COLOR="Red"] 2.6.21.4[/COLOR]** so compiling against them gives you a driver that is not compatible to your running kernel and thus causes the hang.

What you have to do is exchange the headerfiles in the directory of the driver by those that come with your kernel.

The ones you need are scattered in the subdirectories (dvb-core, dvb-usb and frontends) of[COLOR="RoyalBlue"] /usr/src/linux-2.6.23/drivers/media/dvb[/COLOR].

Copy them over the ones that came with the package and recompile the driver.


This is the list of headerfiles to replace:

demux.h
dmxdev.h
dvb_demux.h
dvbdev.h
dvb_frontend.h
dvb_net.h
dvb-pll.h
dvb_ringbuffer.h
dvbt_demod_base.h <---- this was nowhere in the kernel tree!!!
dvb-usb.h
dvb-usb-ids.h

(dvbt_demod_base.h was not in my kernel tree but the driver worked without it)

No luck needed!

Coney

---

### Post by coney on 2008-03-25
Ooops, it wouldn't of course be /usr/src/[COLOR="Red"]linux-2.6.23[/COLOR]/drivers/media/dvb in your case.

That's mine because I have a 2.6.23 but since you have a[COLOR="Red"] 2.6.20[/COLOR] you would have to look under [COLOR="Blue"]/usr/src/[COLOR="Red"]linux-2.6.20[/COLOR]/drivers/media/dvb.[/COLOR]

---

### Post by dessale on 2008-03-26
Just wanted to add my thankyou to stealbanana for his useful hack.

It worked for me on a Realtek device (similar to Freecom Rev 4) which I bought cheaply at a Market.    The Bus ID is 0bda:2831.

So those with similar related devices should give it a try

---

### Post by fall-out on 2008-04-02
Thanks a lot for this workaround, it works very nice with Gutsy. :)

But now I want to install my Freecom DVB-T Stick under Hardy. But there are no .h files, especially not the specified above. :(

> $ ls /usr/src
linux-headers-2.6.24-12  linux-headers-2.6.24-12-generic  rpm

The directories are there, but I it always looks just like that:

> $ ls /usr/src/li*-12/drivers/media/dvb/dvb-usb
Kconfig  Makefile

> $ ls /usr/src/li*-generic/drivers/media/dvb/dvb-core
Kconfig  Makefile

This is what uname -a says:

> $ uname -a
Linux fall-out 2.6.24-13-generic #1 SMP Sun Mar 30 22:57:04 UTC 2008 x86_64 GNU/Linux


From where do I get the original DVB-T driver .h files for my kernel?

---

### Post by fall-out on 2008-04-02
Now I got it! :) I had to get the linux source file via synaptic, extracted the needed .h-files, removed the old module, compiled and installed the new driver. The stick now works without problems with Hardy Beta.

------------------------
**SOLUTION for Hardy Heron resp. Linux Kernel 2.6.24**
for Freecom DVB-T USB-Stick
------------------------

1. Unpack **_[rtl2831u_dvb-usb_v0.0.2mod-HARDY-by-fall-out.tar.gz](http://rapidshare.com/files/104271182/rtl2831u_dvb-usb_v0.0.2mod-HARDY-by-fall-out.tar.gz.html)**_ to any location, e.g. your home folder.
2. cd to dir ./rtl2831u_dvb-usb_v0.0.2mod
3. run $ make and then $ make install



If you had tried [the package from above](http://ubuntuforums.org/showpost.php?p=4371178&postcount=27) then you probably have to remove the incompatbile module first:

> $ sudo rm /lib/modules/2.6.24-12-generic/extra/dvb-usb-rtl2831u.ko
and then reboot with:

> $ sudo shutdown -r now

Then follow the instructions 1 - 3 from above.


GERMAN workaround: [http://forum.ubuntuusers.de/topic/154107](http://forum.ubuntuusers.de/topic/154107)

---

### Post by gaeagles on 2008-04-06
Great,

folowwing your three steps instructions I only had to add

```
sudo modprobe dvb-usb-rtl2831u
```

to at least see my first Linux distro ever recognising my Freecom DVB-T USB rev.4 device.

Still have to find channels though....

Read elsewhere in these forums that you can load the driver module at boot by adding dvb-usb-rtl2831u to the bottom of:

```
gksudo gedit /etc/modules
```

---

### Post by aduncan on 2008-04-09
not having as much luks as everyone else seems to be!

downloaded the freecom drivers and installed them by doing the

make
sudo make install

that all seems to go fine but once ive rebooted and plug the stick in, i get this error in dmesg:

[  530.521199] usb 5-5: new high speed USB device using ehci_hcd and address 4
[  530.654731] usb 5-5: configuration #1 chosen from 1 choice
[  530.721938] dvb_usb_rtl2831u: disagrees about version of symbol dvb_usb_device_init
[  530.721947] dvb_usb_rtl2831u: Unknown symbol dvb_usb_device_init


then my lsmod is:

dvb_usb                19980  0 
dvb_core               80668  1 dvb_usb
i2c_core               26112  1 dvb_usb
usbcore               138632  6 dvb_usb,usbhid,ndiswrapper,ehci_hcd,uhci_hcd

seems to be a few things missing

anyone know how to fix this at all? not really sure what any of the error messages mean!

Thanks!

---

### Post by aduncan on 2008-04-09
dont worry, fixed it! had to reinstall the running linux image

---

### Post by gaeagles on 2008-04-27
> **aduncan said:**
> dont worry, fixed it! had to reinstall the running linux image

And how do you do that, I get these dvb_usb_rtl2831u: disagrees about version of symbol messages after an ```
dmesg | grep dvb
```

I can not install or load the rtl2831u driver module at all (I have a new Hardy install, and in contrast to my previous enthousiastic reports I do not get any sign of life of my device at all (no /dev/dvb, no light on on the stick)

All in all this remains an frustrating issue DVB and Linux, why does it have to be so complicated...

BTW: the error message above, could it be that the problem is dvb_usb_rtl2831u where it should be dvb-usb-rtl2831u?

---

### Post by ugm6hr on 2008-05-03
> **fall-out said:**
> Now I got it! :) I had to get the linux source file via synaptic, extracted the needed .h-files, removed the old module, compiled and installed the new driver. The stick now works without problems with Hardy Beta.

------------------------
**SOLUTION for Hardy Heron resp. Linux Kernel 2.6.24**
for Freecom DVB-T USB-Stick
------------------------

GERMAN workaround: [http://forum.ubuntuusers.de/topic/154107](http://forum.ubuntuusers.de/topic/154107)

I'm toying with the idea of upgrading to Hardy now.  Does this still work with the final Hardy?

PS: Has anyone tried the AMD64 Hardy with this?

EDIT: The rapidshare link doesn't work - try the German forum link for download: [http://forum.ubuntuusers.de/download/9970/](http://forum.ubuntuusers.de/download/9970/)

CONFIRMED:
This works just fine in Hardy 64-bit :)

In the uncompressed folder - just:
```
make
sudo make install
```

---

### Post by Vic Morgan on 2008-05-05
Great! As a simple newcomer, could I ask you you expand that to a Howto? Which folder should it be extracted to, and from where do you do the Make, etc.?
Addendum: Why do I never learn? Did the above, and now my machine won't boot! It's stuck on the Bluetooth installation, which is understandable because I don't have Bluetooth. It seems that in Ubuntu, for every problem encountered, there are many solutions that just create more problems unrelated to the first. At least I still have an XP machine on which to find out how to unfreeze my Ubuntu!

---

### Post by ugm6hr on 2008-05-05
> **Vic Morgan said:**
> Great! As a simple newcomer, could I ask you you expand that to a Howto? Which folder should it be extracted to, and from where do you do the Make, etc.?
Addendum: Why do I never learn? Did the above, and now my machine won't boot! It's stuck on the Bluetooth installation, which is understandable because I don't have Bluetooth. It seems that in Ubuntu, for every problem encountered, there are many solutions that just create more problems unrelated to the first. At least I still have an XP machine on which to find out how to unfreeze my Ubuntu!

:confused:

Not sure why it didn't work for you.  It doesn't matter where you extract the driver to - just run the make etc commands in the same directory.

Are you sure you have the Revision 4 DVB-T stick?  The first 3 revisions are completely different (and need a different driver).

Which version of Ubuntu are you running?

---

### Post by Vic Morgan on 2008-05-15
Sorry for the delay
=========================================
2.6.24-16-generic
============================================
lsusb just hangs, so can't get device ID (included 160 I think),
are the following any use?
==============================================
7: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_14aa_160_0000000000008581_if0
  Unique ID: UfPf.hTTZWOQiWEC
  Parent ID: 2XnU.CeFEN5A9DpC
  SysFS ID: /devices/pci0000:00/0000:00:10.4/usb5/5-1/5-1:1.0
  SysFS BusID: 5-1:1.0
  Hardware Class: unknown
  Model: "DTV Receiver"
  Hotplug: USB
  Vendor: usb 0x14aa "DTV Receiver"
  Device: usb 0x0160 "DTV Receiver"
  Revision: "1.00"
  Serial ID: "0000000000008581"
  Driver: "dvb_usb_rtd2831u"
  Speed: 480 Mbps
  Module Alias: "usb:v14AAp0160d0100dc00dsc00dp00icFFiscFFipFF"
  Driver Info #0:
    Driver Status: dvb_usb_rtl2831u is active
    Driver Activation Cmd: "modprobe dvb_usb_rtl2831u"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #58 (Hub)
==============================================================
[   49.621905] dvb-usb: found a 'Freecom USB 2.0 DVB-T Device' in warm state.
[   49.621993] dvb-usb: will pass the complete MPEG2 transport stream to the sof                                          tware demuxer.
[   49.623242] Modules linked in: dvb_usb_rtl2831u serio_raw dvb_usb parport_pc                                           parport dvb_core psmouse usbhid hid usblp pcspkr nvidia(P) snd_via82xx gameport                                           snd_ac97_codec ac97_bus snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_mpu                                          401_uart snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event s                                          nd_seq snd_timer snd_seq_device snd button soundcore i2c_viapro shpchp pci_hotpl                                          ug i2c_core via_agp agpgart ext3 jbd mbcache sg sr_mod cdrom sd_mod ata_generic                                           pata_acpi floppy via_rhine mii ehci_hcd uhci_hcd usbcore pata_via sata_via r8169                                           libata scsi_mod thermal processor fan fbcon tileblit font bitblit softcursor fu                                          se
[   49.627952] EIP is at rtd2831u_frontend_attach+0xb/0x30 [dvb_usb_rtl2831u]
[   49.630455]  [<e0ac4cf3>] dvb_usb_adapter_frontend_init+0x13/0x100 [dvb_usb]
[   49.630617]  [<e0ac4762>] dvb_usb_device_init+0x322/0x550 [dvb_usb]
[   49.630780]  [<e0c5343c>] rtd2831u_usb_probe+0x1c/0x50 [dvb_usb_rtl2831u]
[   49.632402]  [<e085b018>] rtd2831u_usb_module_init+0x18/0x35 [dvb_usb_rtl2831                                          u]
[   49.637257] EIP: [<e0c536fb>] rtd2831u_frontend_attach+0xb/0x30 [dvb_usb_rtl2                                          831u] SS:ESP 0068:ddea1d84

============================================================

---

### Post by ugm6hr on 2008-05-16
I have no idea why lsusb won't identify the device, but I suspect that means you have a different device.

---

### Post by ugm6hr on 2008-05-18
This is a quote from an email on the dvb mailing:
> There are new drivers posted for the Freecom / Conceptronic / Realtek
cards on:
     [http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2](http://linuxtv.org/hg/~jhoogenraad/rtl2831-r2)
 
		PLEASE FETCH AND TEST THIS VERSION
 
The code as gotten from Realtek, and found on the old link, does not
compile with other current v4l sources anymore. Please stiop using:
     [http://linuxtv.org/hg/~mchehab/rtl2831](http://linuxtv.org/hg/~mchehab/rtl2831)
 
This code is recently synchronised with the mail v4l line, and needs
testing. Compared to the original code, a switch for the IR type is
added. It can now be selected using modprobe. For example if you need
type 2: unload the automatically loaded driver, and reloca the good codes.
 
sudo modprobe -r dvb_usb_rtl2831u
sudo modprobe  dvb_usb_rtl2831u ir_protocol=2
 
-----------------
The following devices are supported (numbers and names do NOT correspond):
grep rtl2831 /lib/modules/2.6.24-16-generic/modules.usbmap | sed -e
's/0x0000.*$//' -e 's/^.*0x0003//'
       0x0bda   0x2831
       0x2304   0x022b
       0x13d3   0x3216
       0x13d3   0x3220
       0x13d3   0x3236
       0x13d3   0x3238
       0x13d3   0x3244
       0x08dd   0x2103
       0x185b   0x0100
       0x1a46   0x1601
       0x14aa   0x0160
 
		 .name = "RTL2831U DVB-T USB2.0 DEVICE",
		 .name = "RTL2831U DVB-T USB2.0 DEVICE",
		 .name = "DVB-T TV-Tuner Card-R",
		 .name = "VideoMate TV U100",
		 .name = "Vestel DVB-T TV Card",
		 .name = "Freecom USB 2.0 DVB-T Device",
		 .name = "DTV-DVB UDTT 7047-USB 2.0 DVB-T Driver",
		 .name = "DTV-DVB UDTT 7047M-USB 2.0 DVB-T Driver",
		 .name = "DTV-DVB UDTT 7047A-USB 2.0 DVB-T Driver",
		 .name = "DTV-DVB UDTT 704L-USB 2.0 DVB-T Driver",
		 .name = "DTV-DVB UDTT 7047Z-USB 2.0 DVB-T Driver",
 
-------------
I have started a second archive for splitting off the tuner code.
For the mxl5005s tuner, this should be straightforward, as the code
found its way into the mainstream v4l already.
 
However, I ran into problems with the mt2060 (which is the tuner I own).
In the function  MT2060_LocateIF1 is making this hard.
This function doe some sort of calibration, and there is both internal
data from the tuner required, and input from the demodulator.
 
I don't see yet how we can put this into the framework of the current
struct dvb_tuner_ops from dev_frontend.h.
 
I'd appreciate some help from somebody more proficient in splitting drivers.
Honestly, I have no idea what all this means.  I'm also loathed to mess with my setup, since it works great already.

---

### Post by blindjudge on 2008-05-23
HELP! tvtime says operation not supported, if I point it at dvr0. I cant even see a menu in Kaffine to watch DVB. And there is no frontend0 device....(I assume this is where I should be point tvtime at)

Cheers (Craig from Australia)


for me:
****************************************************************
dvbt_demod_base.h[COLOR="Red"] <---- this was nowhere in the kernel tree!!![/COLOR]
dvb-usb.h         [COLOR="Red"]<---- this was nowhere in the kernel tree!!![/COLOR]
dvb-usb-ids.h     [COLOR="Red"]<---- this was nowhere in the kernel tree!!![/COLOR]
**********************************************************
craig@Barry:~$ dmesg | grep DVB
[37316.363012] dvb-usb: found a 'RTL2831U DVB-T USB2.0 DEVICE' in warm state.
[37316.363205] DVB: registering new adapter (RTL2831U DVB-T USB2.0 DEVICE)
craig@Barry:~$ dmesg | grep dvb
[37316.363012] dvb-usb: found a 'RTL2831U DVB-T USB2.0 DEVICE' in warm state.
[37316.363020] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[37316.363456] Modules linked in: dvb_usb_rtl2831u dvb_usb dvb_core i2c_core i915 drm ipv6 rfcomm l2cap bluetooth ppdev cpufreq_userspace cpufreq_stats cpufreq_ondemand cpufreq_powersave freq_table cpufreq_conservative dock sbs sbshc container iptable_filter ip_tables x_tables af_packet sbp2 parport_pc lp parport joydev rfkill_input evdev acer_acpi psmouse arc4 serio_raw ecb blkcipher pcspkr uvcvideo b43 compat_ioctl32 videodev v4l1_compat v4l2_common rfkill mac80211 cfg80211 led_class input_polldev battery sdhci ac iTCO_wdt iTCO_vendor_support mmc_core snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm snd_page_alloc snd_hwdep snd_seq_dummy video snd_seq_oss output snd_seq_midi snd_rawmidi snd_seq_midi_event wmi_acer snd_seq snd_timer snd_seq_device button shpchp pci_hotplug snd intel_agp agpgart soundcore ext3 jbd mbcache sr_mod cdrom sg sd_mod ata_piix ata_generic ahci pata_acpi ohci1394 ieee1394 libata scsi_mod ehci_hcd uhci_hcd usbcore ssb tg3 thermal processor fan fbcon tileblit font bitblit softcursor fuse
[37316.363529] EIP is at rtd2831u_frontend_attach+0xb/0x30 [dvb_usb_rtl2831u]
[37316.363566]  [<f8d5fcf3>] dvb_usb_adapter_frontend_init+0x13/0x100 [dvb_usb]
[37316.363583]  [<f8d5f762>] dvb_usb_device_init+0x322/0x550 [dvb_usb]
[37316.363602]  [<f8dd143c>] rtd2831u_usb_probe+0x1c/0x50 [dvb_usb_rtl2831u]
[37316.363742]  [<f8ce2018>] rtd2831u_usb_module_init+0x18/0x35 [dvb_usb_rtl2831u]
[37316.363861] EIP: [<f8dd16fb>] rtd2831u_frontend_attach+0xb/0x30 [dvb_usb_rtl2831u] SS:ESP 0068:ee9bdd84
*****************************************************************
craig@Barry:~$ lsmod | grep dvb
dvb_usb_rtl2831u       92857  1 
dvb_usb                19852  1 dvb_usb_rtl2831u
dvb_core               81404  1 dvb_usb
i2c_core               24832  1 dvb_usb
usbcore               146028  7 dvb_usb_rtl2831u,dvb_usb,uvcvideo,ehci_hcd,uhci_hcd
*****************************************************************
craig@Barry:~$ ls /dev/dvb/adapter0/
demux0  dvr0  net0
*****************************************************************

---

### Post by blindjudge on 2008-05-23
Just did make install of the new one two posts above.

Now I have:

craig@Barry:/dev$ dmesg | grep dvb
[   32.382608] dvb_usb_rtl2831u: disagrees about version of symbol dvb_usb_device_init
[   32.382614] dvb_usb_rtl2831u: Unknown symbol dvb_usb_device_init
[   81.785846] dvb_usb_rtl2831u: disagrees about version of symbol dvb_usb_device_init
[   81.785859] dvb_usb_rtl2831u: Unknown symbol dvb_usb_device_init
craig@Barry:/dev$ lsusb
Bus 005 Device 004: ID 0bda:2831 Realtek Semiconductor Corp. 
Bus 005 Device 003: ID 064e:a101 Suyin Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
craig@Barry:/dev$ lsusb
Bus 005 Device 004: ID 0bda:2831 Realtek Semiconductor Corp. 
Bus 005 Device 003: ID 064e:a101 Suyin Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
craig@Barry:/dev$ 

and no dvb dir in dev?

---

### Post by ugm6hr on 2008-05-30
> **ugm6hr said:**
> I'm toying with the idea of upgrading to Hardy now.  Does this still work with the final Hardy?

Anyone still using this?

I've seen a 2.6.24-17 kernel update.  This will presumably need to be re-compiled, but does it still work OK?

---

### Post by screwt-k on 2008-07-09
Hello everyone,
i'm also using this device,

usb ID:14aa:0160
vendor: conceptronic
DVB-T device
chipe u283..

i tried the package called:rtl2831u_dvb-usb_v0.0.2mod
it compiled, the module is loaded, but the green light doesn't turn on when i plug the device, and the "lsusb" command freez the terminal.

I've also tried to compile with my kernel header version (2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64) but some files are missing in my header tree (dvbt_demod_base.h, dvb-usb.h and dvb-usb-ids.h)

but that didn't change anything.

One last thing, i didn't tried to compile the module via my kernel tool (make menuconfig), i'll now give it a try.

I'm using ubuntu hardy heron (8.04).

Thx for reading.

dmesg
```

[ 3278.176715] usb 2-2: new high speed USB device using ehci_hcd and address 4
[ 3278.257415] usb 2-2: configuration #1 chosen from 1 choice
[ 3278.351682] dvb-usb: found a 'Freecom USB 2.0 DVB-T Device' in warm state.
[ 3278.351831] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 3278.352295] DVB: registering new adapter (Freecom USB 2.0 DVB-T Device)
[ 3278.352507] Unable to handle kernel NULL pointer dereference at 0000000000000000 RIP: 
[ 3278.352510]  [<ffffffff88c93e6e>] :dvb_usb_rtl2831u:rtd2831u_frontend_attach+0xe/0x40
[ 3278.352516] PGD 39408067 PUD 38859067 PMD 0 
[ 3278.352518] Oops: 0002 [1] SMP 
[ 3278.352519] CPU 1 
[ 3278.352520] Modules linked in: dvb_usb_rtl2831u dvb_usb dvb_core af_packet rfcomm l2cap bluetooth ipv6 ppdev powernow_k8 cpufreq_userspace cpufreq_stats cpufreq_conservative cpufreq_ondemand freq_table cpufreq_powersave video output container sbs sbshc dock battery iptable_filter ip_tables x_tables ac sbp2 parport_pc lp parport snd_hda_intel snd_pcm_oss snd_mixer_oss snd_pcm nvidia(P) snd_page_alloc snd_hwdep snd_seq_dummy psmouse snd_seq_oss serio_raw snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd i2c_nforce2 button pcspkr i2c_core shpchp pci_hotplug evdev soundcore k8temp ext3 jbd mbcache sg sr_mod cdrom sd_mod usb_storage libusual pata_acpi pata_amd usbhid hid ohci1394 forcedeth ieee1394 sata_nv ata_generic libata scsi_mod ehci_hcd ohci_hcd usbcore thermal processor fan fbcon tileblit font bitblit softcursor fuse
[ 3278.352551] Pid: 9015, comm: modprobe Tainted: P        2.6.24-19-generic #1
[ 3278.352553] RIP: 0010:[<ffffffff88c93e6e>]  [<ffffffff88c93e6e>] :dvb_usb_rtl2831u:rtd2831u_frontend_attach+0xe/0x40
[ 3278.352557] RSP: 0018:ffff8100397dbc58  EFLAGS: 00010286
[ 3278.352558] RAX: 0000000000000000 RBX: ffff8100397e0d48 RCX: ffffffff8048edd0
[ 3278.352560] RDX: 0000000000000000 RSI: ffffffff80349fa0 RDI: ffff8100397e0d48
[ 3278.352561] RBP: ffff8100397e0000 R08: 0000000000000000 R09: ffff81007f063c10
[ 3278.352562] R10: 0000000000000000 R11: ffffffff803bc920 R12: ffff8100397e0000
[ 3278.352564] R13: 0000000000000000 R14: ffffffff88c9a620 R15: 0000000000000000
[ 3278.352565] FS:  00007fc1a63956e0(0000) GS:ffff81007dc01700(0000) knlGS:00000000f740c720
[ 3278.352567] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
[ 3278.352568] CR2: 0000000000000000 CR3: 0000000039511000 CR4: 00000000000006e0
[ 3278.352569] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[ 3278.352571] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[ 3278.352572] Process modprobe (pid: 9015, threadinfo ffff8100397da000, task ffff8100605fcfc0)
[ 3278.352574] Stack:  ffff8100397e0d48 ffffffff88c7ce13 ffff8100397e0d48 ffffffff88c7c854
[ 3278.352576]  ffff81003940d910 ffffffff88c9b580 ffff810037538800 ffffffff88c9a620
[ 3278.352579]  0000000037538800 ffff810037538800 ffff810037538800 ffff81007d543800
[ 3278.352581] Call Trace:
[ 3278.352585]  [<ffffffff88c7ce13>] :dvb_usb:dvb_usb_adapter_frontend_init+0x13/0x100
[ 3278.352589]  [<ffffffff88c7c854>] :dvb_usb:dvb_usb_device_init+0x3a4/0x5b0
[ 3278.352597]  [<ffffffff88c93bb9>] :dvb_usb_rtl2831u:rtd2831u_usb_probe+0x19/0x50
[ 3278.352609]  [<ffffffff8804833a>] :usbcore:usb_probe_interface+0xda/0x160
[ 3278.352616]  [<ffffffff803bfa6c>] driver_probe_device+0x9c/0x1b0
[ 3278.352620]  [<ffffffff803bfd39>] __driver_attach+0xc9/0xd0
[ 3278.352623]  [<ffffffff803bfc70>] __driver_attach+0x0/0xd0
[ 3278.352626]  [<ffffffff803becad>] bus_for_each_dev+0x4d/0x80
[ 3278.352632]  [<ffffffff803bf0bc>] bus_add_driver+0xac/0x220
[ 3278.352642]  [<ffffffff88047de9>] :usbcore:usb_register_driver+0xa9/0x120
[ 3278.352647]  [<ffffffff8807f01b>] :dvb_usb_rtl2831u:rtd2831u_usb_module_init+0x1b/0x35
[ 3278.352651]  [<ffffffff80263c5e>] sys_init_module+0x18e/0x1a90
[ 3278.352670]  [<ffffffff8020c37e>] system_call+0x7e/0x83
[ 3278.352677] 
[ 3278.352678] 
[ 3278.352678] Code: c6 00 00 c7 40 04 00 00 00 00 c7 40 08 02 00 00 00 48 8b 3f 
[ 3278.352683] RIP  [<ffffffff88c93e6e>] :dvb_usb_rtl2831u:rtd2831u_frontend_attach+0xe/0x40
[ 3278.352687]  RSP <ffff8100397dbc58>
[ 3278.352688] CR2: 0000000000000000
[ 3278.352690] ---[ end trace f807471ef85c6547 ]---
[ 4165.794613] usb 2-2: USB disconnect, address 4


```

lsmod
```

dvb_usb_rtl2831u      101433  1 
dvb_usb                22796  1 dvb_usb_rtl2831u
dvb_core               94380  1 dvb_usb
i2c_core               28544  3 dvb_usb,nvidia,i2c_nforce2
usbcore               169904  9 dvb_usb_rtl2831u,dvb_usb,usb_storage,libusual,usbhid,ehci_hcd,ohci_hcd

```

modinfo
```

filename:       /lib/modules/2.6.24-19-generic/extra/dvb-usb-rtl2831u.ko
license:        GPL
version:        1.0
description:    Driver for the RTL2831U DVB-T USB2.0 devices
author:         ChiaLing
srcversion:     3B5427E9BFABF8943480D17
alias:          usb:v14AAp0160d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1A46p1601d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v185Bp0100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v08DDp2103d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3244d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3238d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3236d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3220d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v13D3p3216d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2304p022Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp2831d*dc*dsc*dp*ic*isc*ip*
depends:        dvb-usb,usbcore
vermagic:       2.6.24-19-generic SMP mod_unload 
parm:           debug:set debugging level (1=info,xfer=2 (or-able)). (debugging is not enabled) (int)

```

---

### Post by jwatsonoz on 2008-07-24
Hi, I'm having problems with my VideoMate U100. The stick is registered just fine but it doesn't tune in with any of the drivers I've found to try. (see output from dmesg and kaffeine below)

lsusb
-----
Bus 003 Device 004: ID 185b:0100 Compro

dmesg | grep dvb
----------------
[ 47.022999] dvb-usb: found a 'VideoMate TV U100' in warm state.
[ 47.023009] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[ 47.053546] dvb-usb: schedule remote query interval to 300 msecs.
[ 47.053555] dvb-usb: VideoMate TV U100 successfully initialized and connected.
[ 47.053580] usbcore: registered new interface driver dvb_usb_rtd2831u


The stick is recognised when I start Kaffeine, but does not tune in. Sample from terminal whilst attempting to tune (it does the same for all frequencies):
...............

Not able to lock to the signal on the given frequency
Frontend closed
dvbsi: Cant tune DVB
Using DVB device 0:0 "Realtek RTL2831 DVB-T"
tuning DVB-T to 585625000 Hz
inv:2 bw:1 fecH:2 fecL:9 mod:3 tm:1 gi:2 hier:0
...............

Not able to lock to the signal on the given frequency
Frontend closed
dvbsi: Cant tune DVB
Transponders: 5
dvbsi: The end
Channels found: 0

Has anybody got a working driver for the videomate u100? Are there plans to create one? thanks

---

### Post by ugm6hr on 2008-10-18
> **ugm6hr said:**
> 
CONFIRMED:
This works just fine in Hardy 64-bit :)

In the uncompressed folder - just:
```
make
sudo make install
```

The latest Hardy kernel is fine too.

Anyone got news on the Intrepid kernel?

Continued here: [http://ubuntuforums.org/showthread.php?t=960113](http://ubuntuforums.org/showthread.php?t=960113)

---

