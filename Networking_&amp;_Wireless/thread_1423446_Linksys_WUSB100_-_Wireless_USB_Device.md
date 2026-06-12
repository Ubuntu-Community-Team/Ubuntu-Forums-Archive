---
title: "Linksys WUSB100 - Wireless USB Device"
date: 2010-03-06
forum: Networking &amp; Wireless
---

### Post by Kyle Vest on 2010-03-06
I have been following a post with wolvie when he was helped with configuring his wireless card (WUSB100) -- I ran the same commands on my computer that he was told to and have the following outputs

iwconfig

wlan3     IEEE 802.11bgn  Mode:Managed  Frequency:2.412 GHz  
          Access Point: Not-Associated   Tx-Power=9 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I have another wireless card that is old and slow that works and it has the following output when using iwconfig:

wlan0     IEEE 802.11b  ESSID:"2WIRE909"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:B3:A1:2E:21   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=14/100  Signal level=14/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Can you please help me.  I am very new to Ubuntu -- and would at least like to be able to have my usb wireless device work.  Thanks!

---

### Post by chili555 on 2010-03-06
> wlan3 IEEE 802.11bgn Mode:Managed Frequency:2.412 GHz
Access Point: Not-Associated Tx-Power=9 dBm It looks like it's working just fine. Have you tried clicking the Network Manager icon and connecting to your network?

---

### Post by Kyle Vest on 2010-03-06
Yes, I can see the network and when I try to connect -- it asks me for the 10 digit code or password.  Which I have typed in over and over...but it tries for about 30 seconds and then says that it cannot connect.  I know that I am using the proper password...thanks for the help.  I noticed on some other threads that some others have had the same problem at this point...but no answers as to what to do.

---

### Post by chili555 on 2010-03-06
Is it a WEP 40/128-bit HEX key? My computer seems to like it better with lower case letters; that is 096c7f etc., and not 096C7F... Have you tried in that manner?

---

### Post by Kyle Vest on 2010-03-07
Yes -- it is a WEP 40/128-bit HEX key -- mine is all numbers.  No letters in the key.  So I don't have any problems with upper or lower case.

---

### Post by chili555 on 2010-03-07
So when Network Manager asks for the key, that's where you put it and then does it connect?

---

### Post by Kyle Vest on 2010-03-07
No - that is the problem.  I put in the key and it thinks for about 30 seconds and never connects.  I am using the same key on use on my windows computers in our house and it just won't work on Ubuntu.  Thanks again for your help.

---

### Post by gordintoronto on 2010-03-07
Right-click the network manager icon, select "edit connections," open the wireless tab, click on "add."  You will need to enter your router's ID, the type of encryption and the router's password.

---

### Post by Kyle Vest on 2010-03-07
Thank you for the help.  I have done what you have asked.  But, still experience the same problem.  I can see the network - it is found by the wireless card.  I go in and edit the setting to include the Hex key.  It tries for 30 seconds and no success.  I tried it all different ways, with no success.

---

### Post by puzzler995 on 2010-03-07
try turning off the Wireless security for a few minutes to see if it will connect without it.

---

### Post by Kyle Vest on 2010-03-08
Thanks for the help.  I turned off the wireless security -- it did show in the network manager as an unsecured network and then I connected with no success.  It did the same thing.  The little circle thing went for about 30 seconds and it never asked me for a password or code.  It just didn't connect.

---

### Post by gordintoronto on 2010-03-08
If there are other strong network signals, try changing the channel on your router.

---

### Post by Kyle Vest on 2010-03-09
None of the above is working.  Just curious do I need a driver or something for this device to work?

---

### Post by gordintoronto on 2010-03-10
If the network shows in network manager, you do not need a driver.  It is built into Linux.

---

