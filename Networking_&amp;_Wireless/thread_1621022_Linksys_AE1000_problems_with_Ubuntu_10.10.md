---
title: "Linksys AE1000 problems with Ubuntu 10.10"
date: 2010-11-13
forum: Networking &amp; Wireless
---

### Post by Raikia on 2010-11-13
Hey, I am new to Ubuntu/Linux, but not at all to computers.  I have googled a lot about getting the Linksys AE1000 wireless usb to work with Ubuntu 10.10, but I am a bit confused.

All the posts I have read so far have their computer not recognizing what the adapter is.  When I run "lsusb", I get (narrowed down to it):

Bus 002 Device 003: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870]


It recognizes the device by name (and I think that "Ralink RT2870" means it already has a driver?), but it won't show up in the "Network Connections".  Even though it says "Ralink RT2870", do I still need to go follow the various directions around for attempting to get it to work?  I am confused because all the other posts I have read only have Ubuntu recognizing it as "Linksys" instead of "Linksys AE1000 v1 802.11n [Ralink RT2870]".

Are there any suggestions?




Also, a "iwconfig" command shows:

lo        no wireless extensions.

eth0      no wireless extensions.


And a "uname -a" shows:

Linux Chris-PC 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux

Thanks so much...I would really appreciate any help.

EDIT:

I got it to work after some fiddling.  Nevermind :-).  If anyone else needs help with this, I can help.  PM me

---

### Post by StaRetji on 2010-11-18
Dude, why don't you share your experience with others.
I don't have that adapter, but people will look for it on google and will find your post.
That's how I fixed my stuff.

Cheers ;)

---

### Post by hodad on 2010-11-23
I agree; please share your method for getting it to work - Thanks!

---

### Post by Raikia on 2010-11-23
1. Go to [http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2) and download "RT3572USB".

2. Unzip the download to a folder.

3. Open up ./include/os/linux_rt.h in a text editor

4. Find/replace "usb_buffer_alloc" with "usb_alloc_coherent" and "usb_buffer_free" with "usb_free_coherent" respectively (there should be only 1 occurance of each)

5. Run "lsusb" and find the Linksys in the list (note the two hex values
Example:
Bus 001 Device 018: ID 13b1:002f Linksys

The "hex" I am talking about (in the example above) is 0x13b1 and 0x002f

6. Open terminal and go to the root of the archive that you unzipped

7. Type 

sed -ir -e 's/^HAS_WPA_SUPPLICANT=n/HAS_WPA_SUPPLICANT=y/' -e 's/^HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n/HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y/' ./os/linux/config.mk

(you can copy and paste, just make sure not to include the quotation marks)

8. Type 

sed -ir -e 's!^#endif // RT2870 //! {USB_DEVICE(0x13B1,0x002F)}, /* Linksys AE 1000 */\n#endif // RT2870 //!' ./common/rtusb_dev_id.c

(Replace "0x13B1, 0x002F" with the hex values you found in step 5. NOTE: They may be these hex values that I supplied)

9. Both step 7 and step 8 should complete without any errors (it shouldn't show any notifications of success either)

10. Type "make && sudo make install"

11. Restart your computer!

---

### Post by elkingrey on 2010-11-23
Can anybody verify these instructions? I have the same problem right now, but with slightly different specs. I don't want to follow these instructions for my computer and be all messed up. 

If I need to I can post my specs on here as well. Or should I start a new topic? Thanks.

---

### Post by Raikia on 2010-11-23
Post your specs in here and I may be able to help you (after about 2 weeks of solid research on this card with linux).

If you try this method, it won't hurt your setup if it doesn't work.  Worst comes to worst, just uninstall it.

---

### Post by elkingrey on 2010-11-23
lsusb gives me

Bus 001 Device 002: ID 13b1:002f Linksys AE1000 v1 802.11n [Ralink RT2870]

iwconfig gives me

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"MBR-135"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:30:44:06:71:35   
          Bit Rate=54 Mb/s   Tx-Power=11 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

uname -a gives me

Linux seth-Dimension-8400 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux

---

### Post by elkingrey on 2010-11-26
Just in case anybody wants to know, I got my problem fixed with all of the details explained in this thread:

[http://ubuntuforums.org/showthread.php?t=1630358](http://ubuntuforums.org/showthread.php?t=1630358)

---

### Post by connork on 2011-01-24
Hey guys,

Got a somewhat similar issue. Using the AE1000 wireless-N adapter as well; I've installed and reinstalled ndisgtk , ndiswrapper, and the amd64 netr28ux.inf driver (win7).

However, running lsusb gives me no device information for the linksys adapter other than:

Bus 001 Device 006: ID 13b1:002f Linksys

Just 'Linksys', no ID information at all. Also:

:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


Anyone run into this before?

---

### Post by lumunofloginism on 2011-02-11
on the second part of the typing
i keep on getting "bash: syntax error near unexptected token `('

---

### Post by walt.smith1960 on 2011-02-11
> **connork said:**
> Hey guys,

Got a somewhat similar issue. Using the AE1000 wireless-N adapter as well; I've installed and reinstalled ndisgtk , ndiswrapper, and the amd64 netr28ux.inf driver (win7).

However, running lsusb gives me no device information for the linksys adapter other than:

Bus 001 Device 006: ID 13b1:002f Linksys

Just 'Linksys', no ID information at all. Also:

:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


Anyone run into this before?

NDISwrapper  only works with Windows XP drivers.  Vista or Win7 drivers won't work AFAIK.

---

### Post by charlieNeb on 2011-02-23
I have the exact same problem with the Linksys AE1000 and Ubuntu 10.10. Though I have been using Linux for years I still consider myself a novice. The forum's suggestions leave me feeling a little overwhelmed. Can someone please break this down. I'm not sure which recommended fixes to follow or if simpler solutions can be found by tweaking settings in something like "Network Connections"... suggestions please.

Just completed the steps in the 4th post. Everything went well but after rebooting I still don't have access to the Linksys. The hex values were the same as example. Did notice that my device was "Device 003"... I am assuming this is not related to the hex values mentioned. Perhaps what is wrong  is Configuring the VPN. I know my SSID but do not understand what is being called for under such things as the BSSID:
Any suggestions on what I should try next?

---

### Post by Rekken on 2011-08-17
> **lumunofloginism said:**
> on the second part of the typing
i keep on getting "bash: syntax error near unexptected token `('
I got the same error.  Instead of editing the code in termninal I edited it in the text file by viewing /os/linux/config.mk and /common/rtusb_dev_id.c as a text document.  

In /common/rtusb_dev_id.c file add {USB_DEVICE(0x13B1,0x002F)}, /* Linksys AE 1000 */ at the bottom of the list of similar items.  And in /os/linux/config.mk file edit HAS_WPA_SUPPLICANT=n to HAS_WPA_SUPPLICANT=y and HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n to HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y.  Then save the file.

I did this after a clean install of Ubuntu 10.10.  Once I updated, I lost connectivity, but as soon as I make && sudo make install I was fine again.

hope this helps.

---

