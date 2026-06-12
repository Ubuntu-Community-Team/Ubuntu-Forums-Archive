---
title: "Sending USSD code to UMTS service provider"
date: 2010-04-18
forum: Networking &amp; Wireless
---

### Post by Sven6210 on 2010-04-18
I have the Huawei E160  UMTS Stick with a German SIM from O2. Actually it is a prepaid tariff where I can buy a daily data flat rate. And I am running Ubuntu 10.04 UNR.

 

 I use SMS to order and confirm a daily data flat rate and I made this working with gammu. Not the most comfortable but a very reliable solution (see [http://ubuntuforums.org/showthread.php?t=1407288](http://ubuntuforums.org/showthread.php?t=1407288)).
 

 In order to charge the my account or to check my account balance I can either use the Original Huawei Software under Windows or I can put the SIM in my mobile and dial a number code.
 

 By entering the code '4444' my UMTS account gets recharged with 10 EUR (debited form my bank account). With the code '*101#'  I can check the account balance.
 

 What I want to do: I want to be able to recharge my account and check my account balance with Ubuntu, so without taking the SIM out and putting it into a mobile phone (and obviously without using the original Windows software).
 

 Using gammu in order to send the necessary codes did not work so far. When entering
 

 gammu --getussd *101# 
  
 I get the following result:
 

 Press Ctrl+C to break... 
 USSD received 
 Status               : No action needed 
 Service reply        : "Unknown error" 
 

 In some threat I have been reading that the the Huawei E160 can not send  USSD encoded data. Instead the device requires PDU encoded data. I also have been reading  that the PDU code 'AA180C3602' represents the USSD code '*101#'. But also using
 

 gammu --getussd AA180C3602
 

 I only get the following result (even if waiting 5 minutes)
 

 Press Ctrl+C to break... 
 

 

 As it seems like I can not use gammu to send USSD code to my network provider I decided to give AT commands a try.
 

 First I start minicom by entering 
  
 minicom -D /dev/ttyUSB1 
  
 

Then I enter:


AT+CUSD=1,"AA180C3602",15 
  
 

and I get the following result:
 

+CUSD:1,"D4313A2D7E83DA6F719A0D9A96E5F6F4B8DC2EBBFD3A450CB47CBBE9EFB0D82C0F9FCB0A19E858A7A3C3E2B2BB652DCBCDFEB3382C5F97D374C50C14AC9BD96172DD7D061DEB7474585C76AFC3727A5941033DE1F4F4DB3D6F87DDE173590E",15 
 

 Encoding the text between the “” on [http://www.twit88.com/home/utility/sms-pdu-encode-decode](http://www.twit88.com/home/utility/sms-pdu-encode-decode) I get the result:
 

 SMSC#A3D2E738ADF617A9D0A9695E6F4F8BCDE2BBDFA354C04BC7BB9EFE0B8DC2F0F9BCA0918E857A3A3C2E2BBB56D2BCDCEF3B83C2F5793D475CC041CAB99D1627DDD760D1BE474785C567FA3C27A7951430D31E4F4FBDD3F678DD1E3795E0
 Sender:
 TimeStamp:// ::
 TP_PID:
 TP_DCS:
 TP_DCS-popis:Uncompressed Text
 class:0
 Alphabet:Default
 

 

 Length:0
 

 So even using PDU and the AT command seems not to work. Does anybody have a solution how I can solve my problem? Any help is welcome.

---

### Post by GeorgeVita on 2010-04-18
Hi **Sven6210**,
PDU strings are more complicated as include other parameters except 'text': length, type, address (sender/receiver numbers), etc
(this info provided but not explained on top of enc/dec page)

Additionally placing just '*101#' to the encoder the result is something ending to 'AA18**2**C3602' and not 'AA18**0**C3602' (using 7-bit encode).
>>> So try AA182C3602 ?

Also trust the AT-commands 'result' you have: +CUSD:**1**,"D4313 ... ",15
which means:
**1 **further user action required (network initiated USSD-Request, or
  further information needed after mobile initiated operation)

(above found within TELIT or WAVECOM AT-COMMANDS REFERENCE .pdf)

Regards,
George

---

### Post by Sven6210 on 2010-04-20
Hi George,

You are right, I tried with the following command in minicom:

AT+CUSD=1,"AA18**2**C3602",15

The result I got was a plain

OK

So it looks like I sent the command the right way. But I did not receive the feedback. Somewhere I read that the 'answer' is send to a different port, however I di not yet find out to which port.

Do you have any idea?

Thank you for your help

Sven

---

### Post by GeorgeVita on 2010-04-20
Hi **Sven6210**,
usually a Huawei modem is configured with 3 ports: /dev/ttyUSB0-1-2
Two of them can be used for data & control.

You can open 3 minicom windows for all /dev/ttyUSBx and 'investigate' modem's behavior.
If modem-manager cause you problems you can:
sudo stop network-manager
sudo killall modem-manager
('sudo start network-manager' resumes above condition)

... I think that 'result' must come to the the same port unless there is an answering SMS or other type of network message ( ? )

If any port 'freeze', reboot.

Regards,
George

---

### Post by Sven6210 on 2010-04-21
Hi George,

Even opening two minicom screens is not helping. I still get a reply I can not convert to readable text - readable for me I mean.

I am close to give up on this issue.

Best regards

Sven

---

### Post by troynall on 2012-06-16
> **GeorgeVita said:**
> Hi **Sven6210**,
usually a Huawei modem is configured with 3 ports: /dev/ttyUSB0-1-2
Two of them can be used for data & control.

You can open 3 minicom windows for all /dev/ttyUSBx and 'investigate' modem's behavior.
If modem-manager cause you problems you can:
sudo stop network-manager
sudo killall modem-manager
('sudo start network-manager' resumes above condition)

... I think that 'result' must come to the the same port unless there is an answering SMS or other type of network message ( ? )

If any port 'freeze', reboot.

Regards,
George


I have an huawei s7 tablet. any idea on how to pinpoint the MODEM port ?

/dev/ttyHS0                           msm_serial_hs
/dev/ttyMSM2                        msm_serial
/dev/smd0                             smd_tty_driver
/dev/smd7                             smd_tty_driver
/dev/smd21                           smd_tty_driver
/dev/smd27                           smd_tty_driver
/dev/smd36                           smd_tty_driver
/dev/smdcntl0                        smd_tty_driver
/dev/smdcntl2                        smd_tty_driver
/dev/smd22                           smd_tty_driver
/dev/smd_pkt_loopback          smd_tty_driver

i got the above serial output from an app called serial.apk
but have no idea which port is the MODEM ?

i am trying to send AT-COMMANDS to my modem.

any help would be much appreciated.

thanks

---

### Post by lisati on 2012-06-16
> **troynall said:**
> I have an huawei s7 tablet. any idea on how to pinpoint the MODEM port ?

/dev/ttyHS0                           msm_serial_hs
/dev/ttyMSM2                        msm_serial
/dev/smd0                             smd_tty_driver
/dev/smd7                             smd_tty_driver
/dev/smd21                           smd_tty_driver
/dev/smd27                           smd_tty_driver
/dev/smd36                           smd_tty_driver
/dev/smdcntl0                        smd_tty_driver
/dev/smdcntl2                        smd_tty_driver
/dev/smd22                           smd_tty_driver
/dev/smd_pkt_loopback          smd_tty_driver

i got the above serial output from an app called serial.apk
but have no idea which port is the MODEM ?

i am trying to send AT-COMMANDS to my modem.

any help would be much appreciated.

thanks

This is an old thread. Because things might have changed in the last year, it might be a good idea to start a new thread.

---

