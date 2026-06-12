---
title: "Scan for channels fails"
date: 2011-06-14
forum: Mythbuntu
---

### Post by natomb on 2011-06-14
Good morning,


I am still working on my first MythTV setup using Mythbuntu. The new release 11.04 does detect my Skystar 

HD2. The "scan" command works properly and detects channels (see attached files in ZAP and VDR format).

However, when trying to teach MythTV about the channels, it fails. Here is what I was trying (using german 

language settings) and what happened.

Full scan (tuned) [Vollständiger Suchlauf (Tuned)] => Error analysing parameters [Fehler beim Analysieren 

der Paramter]

Read from channels.conf [channels.conf einlesen] => No channels found [Keine Sender gefunden]
=> using both formats, ZAP and VDR

Import of existing scan [Importieren eines existierenden Scans] => No channels found [Keine Sender gefunden]

Full scan of all known transponders [vollst. Suchlauf aller bekannten Transponder] => Error setting 

transponder frequency [Fehler beim Einstellen der Transponderfrequenz]

Full scan of single known transponder [vollst. Suchlauf eines bekannten Transponders] => Exception: tune not 

dealt with [Programmierfehler: Tune fertig nicht behandelt]


Can you please advise me what to do? Maybe the easiest would be to provide a working channels.conf file.


Kindest regards
  Bjoern

---

### Post by ian dobson on 2011-06-15
Hi,

I've always had problems getting the mythtv channel scanner to work correctly. I usually just use w_scan to generate a channels.conf file, you just need to use the -X option to create a tzap channels.conf file.

Gruss aus Basel
Ian Dobson

---

### Post by natomb on 2011-06-15
Hi,

I could fix the problem by setting the DiSeq-type for the tuner. Strange thing is that when I tried this option, it did not let me do. I think I pressed something like <Space, Space, Tab, Space, Return, Tab, Return, Space, Space, Return> before the dialog popped up and displayed the selection for LNB.

Now I am working on the situation that the frontend tells me that the tuners are in use and thus I cannot watch TV. But with time I think I will solve this problem, too :D

The error messages read "Fehler: Alle Eingänge sind belegt, aber es gibt keine laufenden Aufnahmen?" (Error: all tuners are busy but there are no recordings)


I hope that once mythtv is up and running, it is "rock-solid". But to get it up and running is a very painful way. Much to do to enable your grandma to setup her own mythtv :)

---

### Post by ian dobson on 2011-06-15
Hi,

No pain, no gain. Setting up Mythtv isn't that easy, but when it's running then it's really nice.

Back to your problem. What do you see in your backend log file (/var/log/mythtv/mythbackend.log)? 

Have you setup the tuner type correctly?
What devices to your see in /dev/dvb?
Can w_scan find any channels?

Regards
Ian Dobson

---

### Post by natomb on 2011-08-28
Just to keep you updated: I have reinstalled the system as "Master backend / frontend" combination and scanning worked from the very first.

I think I will go with the most simple setup, sort out thinks not working and then going to the setup that I really want.

---

