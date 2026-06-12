---
title: "How can I get a Verizon UMW190 to work in 9.10?"
date: 2010-02-13
forum: Networking &amp; Wireless
---

### Post by Billt Joe on 2010-02-13
I tried using the vzaccess manager in wine. that didn't work. So I click on the "enable mobile broadband" button after clicking on the networks notification. I'm not sure how to fill out the wizard so I was hoping someone could help.

here are some screenshots with how far I got.
thanks!

---

### Post by fheinsen on 2010-03-19
I have the same mobile broadband modem and use it regularly without any problems. 

The Verizon UMW190 is a so called "global ready" 3G modem, meaning that it connects to both CDMA and GSM networks.  Alas, Ubuntu 9.10's Network Manager currently identifies this modem as GSM only, so until this gets fixed, connecting over a CDMA network (such as Verizon's network in the US) requires that you use an additional application.

Install "**gnome-ppp**" -- this is the application you will use to connect -- you can find it under Applications -> Ubuntu Software Center, or under System -> Administration -> Synaptic Package Manager.  (Once you have installed it, you may also want to restart your computer to undo anything else you may have done while trying to solve this problem.)  

To use the modem, do the following:

**Step 1.** Plug the modem in.
**Step 2.** Launch gnome-ppp as administrator (e.g., press Alt-F2 and type "gksu gnome-ppp"), and configure the following settings:
 
[LIST]
[*]Modem Tab
[LIST]
[*]Device: /dev/ttyACM0  (in my case, the auto-detect button correctly identified the device)
[*]Type: USB Modem  (do not leave as analog modem!)
[*]Speed: 460800
[*]Phone Line: Tone
[*]Volume: Off
[/LIST]
 
[/LIST]
 
[LIST]
[*]Options Tab
[LIST]
[*]Minimize: checked
[*]Dock in Notification Area: checked
[/LIST]
 
[/LIST]
 Click Close.  Fill in the fields in the main Gnome PPP window:
 
[LIST]
[*]Username: _1234567890@vzw3g.com_   (any 10-digit number works for me)
[*]Password: vzw
[*]Phone Number: #777
[/LIST]
 **Step 3.** Click Connect.  That should be it.


To disconnect, click on the gnome-ppp dock notification icon.

These settings will be saved for the next time you need to connect.

(Hat tip: [http://www.jasons.org/2008/09/02/howto-verizon-um175-usb-evdo-card-under-ubuntu-hardy/](http://www.jasons.org/2008/09/02/howto-verizon-um175-usb-evdo-card-under-ubuntu-hardy/))

---

### Post by alexfish on 2010-03-20
> **Billt Joe said:**
> I tried using the vzaccess manager in wine. that didn't work. So I click on the "enable mobile broadband" button after clicking on the networks notification. I'm not sure how to fill out the wizard so I was hoping someone could help.

here are some screenshots with how far I got.
thanks!

hi

if the Network Manager does not have the details then ask your service provider

it would be interesting to see the outputs of these commands entered from the termial

Code:

dmesg | grep -e "modem" -e "tty" 

this will show the ports been used and the type of modem

Code:

tail -f /var/log/syslog

this will show the activity of  the main system log
 
 The Network Manager also has a database called  [FONT=monospace][/FONT]serviceproviders.xml this can be edited to suit your ISP  , there is also the option of providing info of type of connection IE: CDMA or GSM etc

Details here

[http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders](http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders)

also if you do not wish Gnomeppp   at "user level "and not " superuser check "these out

[PPP  Connection Utilities]("http://www.pcurtis.com/ubuntu-mobile.htm#gnomeppp")
[LIST]
[*][The gnome-ppp  dialer utility]("http://www.pcurtis.com/ubuntu-mobile.htm#gnomeppp")
[LIST]
[*][User  Priviledges- the dip and dialout groups ]("http://www.pcurtis.com/ubuntu-mobile.htm#dip_dialout")
[*][Permissions  for /etc/ppp/pap-secrets and etc/ppp/chap-secrets]("http://www.pcurtis.com/ubuntu-mobile.htm#ppp_secrets")
[*][Adding  the initial Signal Strength to the gnome-ppp connection log ]("http://www.pcurtis.com/ubuntu-mobile.htm#signal_strength")
[/LIST]
[/LIST]

---

### Post by kwatson512 on 2010-04-23
I'm having the same problems, and am a little cautious about installing gnome-ppp.  Synaptic says if I do so it will uninstall resolvconf.  Will that mess up my other "normal" connections that I depend on Network Manager for?

BTW, I've installed usb-modeswitch to get Network Manager to recognize the modem part of the UMW190, and that works well, but NM wants to create a GSM Mobile Broadband connection.  And like others, I don't know what to plug in to the APN blank.

Running Linux Mint 8 (based on Ubuntu 9.10) on a Lenovo x200 laptop: Intel Core2 Duo CPU P8600@2.40GHz, 3 GB RAM

---

### Post by alexfish on 2010-04-23
Hi

The Network Manager should handle cdma and gsm connections , it is a front end to ppp

For APN check with your ISP , also for all details to be entered if they are not listed , also ask them for the numerical addresses of their named servers , these can be entered DNS servers box when IVp4 is set to Automatic (PPP) address only, helpful if the network manager fails to return the addresses of the named servers .

Also note , as you say installing gnomeppp wants to remove  resolvconf , also if you have gnomeppp installed then installing resolvconf will want to remove gnomeppp or wvdial
however do not get confused with the etc/resolv.conf or the etc/ppp/resolv.conf

added

have a look at this post  #[**21**]("http://ubuntuforums.org/showpost.php?p=8809834&postcount=21")  as regards Network Manager (How to update the Network Manager database.)/also examine the file mentioned (serviceproviders.xml ) note the difference between gsm and cdma ,

found a thread here , may be of help , may be the post at #21 not required

[http://ubuntuforums.org/showthread.php?t=963529](http://ubuntuforums.org/showthread.php?t=963529)

---

### Post by kwatson512 on 2010-04-23
@alexfish, thanks for the suggestions, but I'm still stuck.  I tried the procedure at the [thread]("http://ubuntuforums.org/showthread.php?t=963529") you mentioned, but NM still tries to connect the UMW190 to a GSM network, even though the device is configured for CDMA.  

Could it be that the usb_modeswitch script is flagging the device incorrectly, setting it up to NM as a GSM device?  My specific product code isn't in the usb_modeswitch database (so my hardware isn't actually supported), but there is a close match:

```
########################################################
# UTStarcom UM185E (distributor "Alltel")

DefaultVendor= 0x106c
DefaultProduct=0x3b06

TargetVendor=  0x106c
TargetProduct= 0x3717

CheckSuccess=20

MessageContent="55534243b82e238c24000000800008ff020000000000000000000000000000"
```

lsusb identifies my vendor as 0x106c and the device as 0x3b05.  
Does the "MessageContent=" line identify the type network and set up strings?  Do you have an example of a MessageContent string I could use to dial Verizon over CDMA?

I spent a bit of time on the phone with Verizon Wireless tech support, and they have never heard of APN.  Looking at the [Service Provider Database]("http://live.gnome.org/NetworkManager/MobileBroadband/ServiceProviders") on the NetworkManager site, I learned that CDMA networks don't use APN.

Also, I don't understand your answer about resolvconf.  You confirmed that installing gnome-ppp will remove resolvconf, but didn't tell me whether that was good or bad for NM.  I need NM for wired and wifi connections more than I need mobile broadband, but there are occasions when mobile broadband is the only option.

Here are the results of a couple of information gathering commands:

```
$ dmesg | grep -e "modem" -e "tty"
[    0.001207] console [tty0] enabled
[    0.960169] 0000:00:03.3: ttyS0 at I/O 0x1830 (irq = 17) is a 16550A
[13992.007142] cdc_acm 2-2:1.0: ttyACM0: USB ACM device
[13992.009585] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[16192.714060] cdc_acm 2-2:1.0: ttyACM1: USB ACM device
```

```
$ tail -f /var/log/syslog
Apr 23 22:08:19 kwatson-lnx02 modem-manager: Got failure code 100: Unknown error
Apr 23 22:09:20 kwatson-lnx02 NetworkManager: <WARN>  stage1_prepare_done(): GSM modem connection failed: (32) Network timeout
Apr 23 22:09:20 kwatson-lnx02 NetworkManager: <info>  (ttyACM1): device state change: 4 -> 9 (reason 1)
Apr 23 22:09:20 kwatson-lnx02 NetworkManager: <info>  Marking connection 'Verizon Mobile Broadband' invalid.
Apr 23 22:09:20 kwatson-lnx02 NetworkManager: <info>  Activation (ttyACM1) failed.
Apr 23 22:09:20 kwatson-lnx02 NetworkManager: <info>  (ttyACM1): device state change: 9 -> 3 (reason 0)
Apr 23 22:09:20 kwatson-lnx02 NetworkManager: <info>  (ttyACM1): deactivating device (reason: 0).
Apr 23 22:09:20 kwatson-lnx02 NetworkManager: <info>  (eth0): writing resolv.conf to /sbin/resolvconf
Apr 23 22:09:20 kwatson-lnx02 NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Apr 23 22:17:01 kwatson-lnx02 CRON[4503]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

---

### Post by alexfish on 2010-04-23
hi 

can you post the results of the lsusb command from the terminal, this should show the exact  ID's of  the device, however, if the device is recognised with NM then it would seem feasible to connect to the Internet either from NM or wvdial or Gnome ppp (front end to wvdial), NM and the developers have been requesting input for x.time from ISP's 

Verizon , what can I say, cdma is one of the most accessible forms of modern day communications as regards modems and the internet, Education and Training is supposed to be . What? , quite possibly told " if you hear the word Linux " answer " Don,t know , act dumb, this is normally a forward process for PPP , the protocols are the same for windows and  for  Linux 

Sorry for the rant 

will post further on the resolvconf or the resolv.conf. time for ZZZZZ.

regards

alexfish

---

### Post by alexfish on 2010-04-24
Hi kwatson512

Had Time to look through the messages etc

don't know if the modeswitch is required for this device ( yet the ID's point to the device you have mentioned ) one possibility is that the modeswitch is resetting the device, you could try uninstalling usb_modeswitch and see what happens to the ID's

For now it looks as if the modem is recognised on ttyACM zero and one, and the drivers have loaded 

[13992.007142] cdc_acm 2-2:1.0: ttyACM0: USB ACM device
[13992.009585] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[16192.714060] cdc_acm 2-2:1.0: ttyACM1: USB ACM device

 Looking at the error message Activation failed presents another problem

Here is a list 

1. have you activated the device with Verizon, if not ask Verizon to activated your modem / follow their advice , it may have to be done in windows

here is the the brickwall you are facing  with NM assuming the device has been activated

2.  if your connection requires an sid  (for your area)check with verizon, then you maybe able to find the operator and the sid  listed in the providers database , so  you may be able to pick this up via the wizard .if not you may be able to enter the details in the database. as previously mentioned, and hope NM connects to the correct tty

3. as you can see from the posts most prefer using wvdial or gnomeppp. Yep , the problem you have is the resovconf this is a piece of software available in the repo's(check to see if it is installed), as the name suggests is a name server handler something that this type of connection does not require( I think). although some suggest it's use for certain connections including mobile networks.For now if you have to opt for the use of gnomeppp or wvdial then it looks as if no options are available but to remove the said piece of software (there may be other options available but would need to check this out, have you configured and used this program, if so make a backup any configurations you have,before removing the software, one reason some prefer gnomeppp is that it should detect the modem and use the correct port

regards

alexfish

---

### Post by kwatson512 on 2010-04-24
Yeah, modeswitch was a red herring. I removed it but that didn't change the behavior of NM.  NM still thinks the device is GSM.  BTW, I did activate it with Verizon under Windows and it works perfectly there.

I guess my only option at this point is to try gnome-ppp.  I'll report back.

---

### Post by alexfish on 2010-04-24
possibly one way to verify the types of connections the modem uses is to use a serial terminal such as minicom , when set up

the  ATI or AT+GCAP command  may reveal some details about the device

ATI.........       Identification 
AT+GCAP   Request Complete Capabilities List 


Added :

I have looked up this device here is  part of the extract

The Verizon Wireless UMW190  comes to the market with 3G connectivity, and is capable of delivering  high-speed Internet. The gadget features support for Dual-Band CDMA  Revision A (Rev. A), Tri-Band UMTS / HSPA and Quad-Band GSM / GPRS /  EDGE frequencies, which makes it fit for use anywhere around the world. 

so maybe the above AT commands may reveal what is shown in the extract, thinking thoughts ' is it meant to be used as gsm or cdma etc  or is it making its own choice, or has this been set by the configuration in windows. mmm . can you double check this. in windows what does the phone number show in connection details, also get as much info from network connection / properties




regards

alexfish

---

### Post by kwatson512 on 2010-04-24
I installed gnome-ppp and successfully configured it to make a GSM connection on the Verizon network.  However, I can't get vpnc to work to establish a vpn tunnel to my corporate network (which is also a requirement).  Network Manager is really elegant in that vpnc can be seamlessly integrated into it.  

I sudo launched vpnc in a terminal, and provided all the requested inputs, but authentication failed after several nuanced attempts.

So I can't use this like I need to, but I have been able to get the UMW190 to connect over GSM.

---

### Post by alexfish on 2010-04-24
Good news and some not so good news on the vpn

could you post the details of how  you configured the connection in gnomeppp as it may help others

don't know if this link will help with the vpn

[http://support.real-time.com/linux/dialup/wvdial.html](http://support.real-time.com/linux/dialup/wvdial.html)

also have a look in your repo's search vpn and look at pptpd and possibly others

thanks in advance

alexfish

---

### Post by kwatson512 on 2010-04-24
I'm marking this solved.  I'm replying now over the ppp connection through my vpn tunnel!  There are a couple of tricks, so I'll try to explain how I got it to work.  You will need gnome-ppp, which is available in the repositories.

First, when you plug the UMW190 in, it starts in storage mode, and the icon for Verizon Access Manager (a Windows program) appears on your desktop. Right-click on the icon and select <Eject> (not <Unmount> or <Safely remove drive>).  That "ejects" the storage partition, allowing the modem partition to connect.

Second, follow the procedure at [this post]("http://ubuntuforums.org/showpost.php?p=8996651&postcount=2").  Hat tip to fheinsen!

For those that need a vpn tunnel in addition to a mobile broadband connection, network-manager-vpnc will not work since this connection was not made through network manager.  For that, follow the procedure at [this link]("http://www.debuntu.org/how-to-connect-to-a-cisco-vpn-using-vpnc").  The trickiest part of this is decoding the group password, but if you have enabled network-manager-vpnc you have already solved that problem.  :)

Once established, you can create a vpnconf file as described in the last link to partly automate the vpn connection process, and you can add a launcher to the panel for gnome-ppp.  

Just a little command line fun, but it's better than being stuck somewhere without wifi and no way to connect!

---

### Post by Byzandula on 2010-04-28
This is a great thread. I just got my Toshiba NB305-N310 netbook up and running on 10.04 and can confirm that these directions also work for the UMW190 on Lucid.

Cheers!

---

### Post by blueridgedog on 2010-11-12
I an using the UMW190 with gnome-ppp.  I have access to GSM and CDMA networks here in the US.  Is there a way to tell which network it is using?  I don't want a big data roaming bill at the end of the month.

---

