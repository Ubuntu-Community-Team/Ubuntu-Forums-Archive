---
title: "Modem not recognized"
date: 2005-12-30
forum: Networking &amp; Wireless
---

### Post by DarkW0lf on 2005-12-30
5610 56k FaxModem USR 56k Internal WinModem

Dell Optiplex

I have been researching this and found several posts similar to my system.
With the one exception that they all have posted they hyave a hardware modem, I think I may have a problem with mine reporting as a Winmodem

lspci output:

0000:00:0e.0 Comuunication controller: 5610 56k FaxModem USR 56k Internal WinModem

Am I out of luck, is this really an unsupported software modem ?

---

### Post by towsonu2003 on 2005-12-30
it was a very good idea to attach modemdata.txt :)

although I seem to never be able to decrypt what modemdata.txt says, these look interesting (for others who know how to read it): > Modem candidates are at PCI_buses:  0000:00:0e.0
    
Providing detail for device at  0000:00:0e.0
  with vendor-ID:device-ID
	    ----:----
Class 0780: 12b9:1007   Communication controller: 5610 56K FaxModem USR 56k Internal WinModem
  SubSystem 12b9:00c2  5610 56K FaxModem: Unknown device 00c2

:1007    ERL3263A-0 DF GWPCI PC99  WinModem  **no Linux support**

The following may be supported  by Conexant drivers at   [http://www.linuxant.com](http://www.linuxant.com)
   14f1:2f12 (3COM/USR model 3094-3095)
   14f1:2f13 (USR OEM)
   14f1:2f14 3COM/USR
 though they carry USR labels.

although this is not promising at all, to me, your best bet is to send an email to linmodems.org mailing list and see what they think... please do not forget to attach the modemdata.txt and to follow this instruction when mailing: >  DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.10 "Breezy Badger"  kernel 2.6.12-9-386
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]

other than this, I have no clues... sorry :(

---

### Post by DarkW0lf on 2006-01-01
I have sent a message to linmodems.org and checked their archives.
I haven't found a response their nor received a reply to my email.

<ModemData>

 12b9 is US Robotics. acquired by 3COM
       :0062    erk41926a-0.6 usr 56k internal modem
       ;1006    3cp803598  Voice          WinModem  no Linux support
       :1007    ERL3263A-0 DF GWPCI PC99  WinModem  no Linux support
       :1008    3cp803598  is Supported by the standard:  serial.o

</ModemData>

See 0062 and 1008
How am I too take it ?
Only half the entries say they are not supported, what about the other half ?

And I have no idea how to go about compiling my own drivers.

---

### Post by towsonu2003 on 2006-01-01
I HATE to do this but: > Sorry to deliver bad news, but your US Robotics has no
linux support:

 Class 0780: 12b9:1007   Communication controller:
 5610 56K FaxModem USR 56k Internal WinModem
   SubSystem 12b9:00c2  5610 56K FaxModem: Unknown
 device 00c2
       :1007    ERL3263A-0 DF GWPCI PC99  WinModem  no
Linux support.  Check for other alternatives.

this is from [http://archives.linmodems.org/21314](http://archives.linmodems.org/21314)

sorry...

---

### Post by DarkW0lf on 2006-01-02
I hate to do this but...   that's not my email.

I see he has the same hardware, well looks like I may have to find another way.
I'll have to post my other idea and see if I can get that to work.

---

### Post by towsonu2003 on 2006-01-02
[QUOTE=towsonu2003]I hate to do this but...[/QUOTE] I meant "I hate to give you bad news"

What's your other idea?

---

### Post by DarkW0lf on 2006-01-23
Look for the thread on using WinXP as a Gateway.

---

