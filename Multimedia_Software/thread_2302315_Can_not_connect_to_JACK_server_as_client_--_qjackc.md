---
title: "Can not connect to JACK server as client -- qjackctl"
date: 2015-11-09
forum: Multimedia Software
---

### Post by Will_A on 2015-11-09
Hey everyone,

I am trying to use qjackctl in order to support ALSA with supercollider, a music programming / composition language.  

I am running on Ubuntu 14.04 Trusty.  [I installed supercollider in the fashion of this tutorial]("https://scacinto.wordpress.com/2014/02/04/new-supercollider-on-xubuntu/") in case anyone wants to follow along and knows about supercollider.  

I try to start a JACK server with this command:
```
 $ qjackctl 
```

After hitting Start on QjackCtl's little GUI,  I get these messages in a dialog from qjackctl.  

```
[COLOR=#999999]12:00:08.418 Patchbay deactivated.[/COLOR][COLOR=#999999]12:00:08.420 Statistics reset.[/COLOR]
[COLOR=#cccc99]12:00:08.425 ALSA connection change.[/COLOR]
[COLOR=#999999]12:00:08.440 D-BUS: Service is available (org.jackaudio.service aka jackdbus).[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
[COLOR=#66cc99]12:00:08.449 ALSA connection graph change.[/COLOR]
[COLOR=#ff0000]12:00:15.153 D-BUS: JACK server could not be started. Sorry[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
Mon Nov  9 12:00:15 2015: Starting jack server...
Mon Nov  9 12:00:15 2015: JACK server starting in realtime mode with priority 10
Mon Nov  9 12:00:15 2015: ERROR: Cannot lock down 82274202 byte memory area (Cannot allocate memory)
Mon Nov  9 12:00:15 2015: ERROR: cannot register object path "/org/freedesktop/ReserveDevice1/Audio0": A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
Mon Nov  9 12:00:15 2015: ERROR: Failed to acquire device name : Audio0 error : A handler is already registered for /org/freedesktop/ReserveDevice1/Audio0
Mon Nov  9 12:00:15 2015: ERROR: Audio device hw:0 cannot be acquired...
Mon Nov  9 12:00:15 2015: ERROR: Cannot initialize driver
Mon Nov  9 12:00:15 2015: ERROR: JackServer::Open failed with -1
Mon Nov  9 12:00:15 2015: ERROR: Failed to open server
Mon Nov  9 12:00:16 2015: Saving settings to "/home/wilach/.config/jack/conf.xml" ...
[COLOR=#ff0000]12:00:22.652 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
```


I've seen other posts regarding qjackctl ask for system info, so here is

**_lspci:_**
```
00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
00:1c.4 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #5 (rev e3)
00:1d.0 USB controller: Intel Corporation Wildcat Point-LP USB EHCI Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
06:00.0 Network controller: Intel Corporation Wireless 3160 (rev 83)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)

```

I've looked around for this particular issue and didnt find all that much.  Anyone know what is going on?  If any more info is needed, I can provide.  

Thanks a million!

---

