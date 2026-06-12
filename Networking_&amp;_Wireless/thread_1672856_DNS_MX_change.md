---
title: "DNS MX change"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by arvindm on 2011-01-21
Hi
I am new to DNS bind need some help on adding MX for a different domain into a zone.

I have zone file for example abc.com and is listed below. Currently MX is 69.x.x.x
I got to a request to change MX to mail residing outside means is in different domain. 

Details are below
MX preference = 1, mail exchanger = MIDDLEBURYINTERACTIVE.COM.S10A1.PSMTP.com
MX preference = 2, mail exchanger = MIDDLEBURYINTERACTIVE.COM.S10A2.PSMTP.com

I tried adding names and even with IP address to which these resolves but nothing worked could be I am missing some syntax. Any input/help will be appreciated -Thnx

; abc.com
;
; --------------------------------------------------------------------------
; $Id$
; Change History:
;
; 20080926 xxxxxxxx      zone file created
; 20081015 xxxxxxxx     Modified MX
; 20091117 xxxxxxxx     Added A record for 
; 20091120 xxxxxxxx     Added A record for 
; 20091221 xxxxxxxx     Added A record for 
;
; --------------------------------------------------------------------------
;
$INCLUDE        master/SOA
$INCLUDE        master/NS
$INCLUDE        master/mx-abc
$INCLUDE        master/www-abc
$INCLUDE        master/community
smtpr2                  IN      A       69.x.x.x


================ 

[root@ns master]# more mx-abc

; created on 10/15/08 by 
;
; --------------------------------------------------------------------------
; $Id$
; Change History:
; 20081015 
; 20081028 
; 20100120 
; --------------------------------------------------------------------------
@       MX      10      smtpr2
smtpr2          A       69.x.x.x
mail    CNAME   smtpr2

==================

---

### Post by SeijiSensei on 2011-01-21
In mx-abc replace

@ MX 10 smtpr2

with 

@    MX   0 MIDDLEBURYINTERACTIVE.COM.S10A1.PSMTP.com
@    MX   5 MIDDLEBURYINTERACTIVE.COM.S10A2.PSMTP.com

The 0/5 determine the order in which the servers are accessed.  The actual values don't matter; it's purely ordinal.

You might not need the second @ sign.  I don't know what software you're using.  I write all my bind9 zone files by hand, so I'm unfamiliar with the configuration you have here.  You want to end up with something like

```

@     IN   SOA   middleburyinteractive.com. postmaster.middleburyinteractive.com. {

[stuff]

      IN    MX   0 MIDDLEBURYINTERACTIVE.COM.S10A1.PSMTP.com
      IN    MX   5 MIDDLEBURYINTERACTIVE.COM.S10A2.PSMTP.com

[more stuff]

```

---

### Post by arvindm on 2011-01-21
Thanks for the reply  much appreiciated.  What I added which did not work was similar and I have listed below. Result what I was getting was abc.com was getting added  as sufix to these records listed below when I quireid mx for abc.com. Also they were showing no ip address. I checked some forums and noticed I had to end the entries with a period. Similar I saw on ur answer. Also there is a entry for same smtpr under zone file do I have to remark that too as when I did this change it was doing load balancing between new ones and old one 69.x.x.x. I rolled back and then posted on forum to get some help. Can you please check this and provide correction what I need to do on this file or shall I just replace what you provided as I do see you have ended first statement with a period and what is reffered as stuff or more stuff.
thnx
 
[root@eq-ns3 master]# cat mx-abc
;
;
; --------------------------------------------------------------------------
; $Id$
; Change History:
; 20081015 
; 20081028 
; --------------------------------------------------------------------------
;@       MX      10      smtpr2
;smtpr2          A       69.x.x.x
;mail    CNAME   smtpr2

@       MX      10      MIDDLEBURYINTERACTIVE.COM.S10A1.PSMTP.com
        MX      20      MIDDLEBURYINTERACTIVE.COM.S10A2.PSMTP.com
        MX      30      MIDDLEBURYINTERACTIVE.COM.S10A2.PSMTP.com
        MX      40      MIDDLEBURYINTERACTIVE.COM.S10B2.PSMTP.com

---

### Post by arvindm on 2011-01-21
Just to be simple this is the file I came up, will this work. I am keeping old one to just check if I see all MX records once I see in query/lookup I will remove the first one.
Please let me know thnx
 
[root@master]# cat mx-powerspeak
; 
; --------------------------------------------------------------------------
; $Id$
; Change History:
; 20081015 
; 20081028 
; --------------------------------------------------------------------------
;@       MX      10      smtpr2
;smtpr2          A       69.x.x.x
;mail    CNAME   smtpr2

@       MX      10      smtpr2
        MX      20      MIDDLEBURYINTERACTIVE.COM.S10A1.PSMTP.com.
        MX      30      MIDDLEBURYINTERACTIVE.COM.S10A2.PSMTP.com.
        MX      40      MIDDLEBURYINTERACTIVE.COM.S10A2.PSMTP.com.
        MX      50      MIDDLEBURYINTERACTIVE.COM.S10B2.PSMTP.com.
smtpr2          A       69.x.x.x
mail           CNAME    smtpr2

---

### Post by SeijiSensei on 2011-01-22
> **arvindm said:**
> Thanks for the reply  much appreiciated.  What I added which did not work was similar and I have listed below.

Try putting "@" in front of each line.  In a DNS zone file, the @ is an alias for the domain itself.  In a complete zone file, it's only needed once at the beginning.  Everything else uses it by default as in the example I posted above.  Since you're not creating a complete zone file, you might need to use the @ for every MX record the way the original entry you posted does.

---

### Post by arvindm on 2011-01-22
I did use this one and it works. For test purpose I kept the existing as preferred and will take it off during cutover. What I was missing was period for each mx entry for external domain. Yes one @ is working. Thanks for all ur responses and help. 
 
[root@master]# cat mx-powerspeak
; 
; --------------------------------------------------------------------------
; $Id$
; Change History:
; 20081015 
; 20081028 
; --------------------------------------------------------------------------
;@       MX      10      smtpr2
;smtpr2          A       69.x.x.x
;mail    CNAME   smtpr2

@       MX      10      smtpr2
        MX      20      MIDDLEBURYINTERACTIVE.COM.S10A1.PSMTP.com.
        MX      30      MIDDLEBURYINTERACTIVE.COM.S10A2.PSMTP.com.
        MX      40      MIDDLEBURYINTERACTIVE.COM.S10A2.PSMTP.com.
        MX      50      MIDDLEBURYINTERACTIVE.COM.S10B2.PSMTP.com.
smtpr2          A       69.x.x.x
mail           CNAME    smtpr2

---

