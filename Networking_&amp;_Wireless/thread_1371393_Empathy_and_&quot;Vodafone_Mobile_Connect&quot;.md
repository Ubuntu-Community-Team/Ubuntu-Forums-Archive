---
title: "Empathy and &quot;Vodafone Mobile Connect&quot;"
date: 2010-01-03
forum: Networking &amp; Wireless
---

### Post by satriaulie on 2010-01-03
Hi everyone! I need some help here. :-)
I've finally got "Vodafone Mobile Connect"(VMC, from now on) installed on my Ubuntu Karmic. It makes it possible for me to take advantage of my "Huawei" mobile broadband dongle. Sms services and such.

The problem is however that when my computer is online through "VMC" Empathy thinks I'm offline, so I can't connect to MSN and such.

I guess this has to do with the integration with "Network Mannager", but is there a workaround? So that "Empathy" will recognize me as online even though "Network Manager" shows me as offline?

---

### Post by alexfish on 2010-01-03
> **satriaulie said:**
> Hi everyone! I need some help here. :-)
I've finally got "Vodafone Mobile Connect"(VMC, from now on) installed on my Ubuntu Karmic. It makes it possible for me to take advantage of my "Huawei" mobile broadband dongle. Sms services and such.
 
The problem is however that when my computer is online through "VMC" Empathy thinks I'm offline, so I can't connect to MSN and such.
 
I guess this has to do with the integration with "Network Mannager", but is there a workaround? So that "Empathy" will recognize me as online even though "Network Manager" shows me as offline?
 
 
Hi
 
on vodafone what type of pay plan  are you on
 
also , you trying to chat,   text , Email, on line from your desk top

---

### Post by satriaulie on 2010-01-03
I only use the application "Vodafone Mobile Connect". My internet provider is Netcom (Norway).

The problem is that by default internet using aplications are looking for "Network manager" to tell them that the computer is online.
I need a fix that either tells "Network Manager" that it is online or a fix that tells the other applications to ignore "Network Manager"s status.

---

### Post by alexfish on 2010-01-03
> **satriaulie said:**
> I only use the application "Vodafone Mobile Connect". My internet provider is Netcom (Norway).

The problem is that by default internet using aplications are looking for "Network manager" to tell them that the computer is online.
I need a fix that either tells "Network Manager" that it is online or a fix that tells the other applications to ignore "Network Manager"s status.

Hi

Need to ask some Questions

How are you connecting at present; Gnomeppp,Network manager or other

From the terminal

Code;

lsusb


then

Code;

dmesg | grep -e "modem" -e "tty"

then post details of above

---

### Post by satriaulie on 2010-01-03
I see! :-)
 Now I'm connected with network manager and the Huawei usb modem.

---

### Post by unclejac on 2010-01-03
Does Pidgin instant messenger work instead? 

if it is not already installed

```
sudo apt-get install pidgin
```


had problems tonight with Empathy connecting to the network too, on a EEE PC using 9.10 UNR.

Working fine with Pidgin.

---

### Post by satriaulie on 2010-01-03
Pidgin is working until you restart your computer. :-)

Yes I've tried it.

I repeat: :-)
The problem is not empathy or Pidgin. Firefox can also have the same problem. It's not anything wrong with Huawei or VMC.

The problem is that NM is offline and gives that message to all the other apps.
So either the other apps must be set to ignore the offline message from NM or NM must be set to appear online.
I don't know how to do any of the actions.

So if I connect to the internet using NM and the Huawei everything works perfectly, but I loose the possibility to send and receive sms through my network providers simcard.

If I connect to the internet using VMC and the Huawei I still can browse the web through google chrome.
So again the problem is that NM doesn't know that I'm in fact online and sends that message to the rest of the apps. :-)

Sorry for repeating myself all the time, but is the problem clear now?
:-)

So if someone knows how to hack NM to stay in online mode even when offline, that would be great! :-)

---

### Post by alexfish on 2010-01-03
hi

some vodafone payment plans  have restrictions

   if you are uk and on top and go ,sending sms is not possible . i will look into how it may work to receive them

   need to Know your Type of Plan

---

### Post by satriaulie on 2010-01-03
Well I'm back :-)

Just figured out that this really is a DBus problem.
Well not really a problem, but a headache.

The best thing would be to be able to send sms's via the simcard without VMC, and have NM handling all network connections.

Anuone with a solution to that? :-)

---

### Post by peterthewolf on 2010-01-03
Do not use anything that will help BUT I have found as a general rule that if network manager is causing problems the best way to get round the problem is to replace network manager with WICD it is in repos.

---

### Post by satriaulie on 2010-01-03
> **alexfish said:**
> hi

some vodafone payment plans  have restrictions

   if you are uk and on top and go ,sending sms is not possible . i will look into how it may work to receive them

   need to Know your Type of Plan

I'm sorry, but I don't really think you understand the problem.

First of all I'm in Norway.
I use Netcom, not Vodafone. Vodafone is just the name of the program.
Sms is working perfectly in the mentioned Vodafone program.

Anyway the problem is Network Manager and DBus.

---

### Post by satriaulie on 2010-01-03
> **peterthewolf said:**
> Do not use anything that will help BUT I have found as a general rule that if network manager is causing problems the best way to get round the problem is to replace network manager with WICD it is in repos.

Yes I've been thinking about that, but I'm trying to keep the installation as clean as possible. I'm looking for ways to setup the system as easy as possible, so that new users will feel that leaving Windows is a breeze. :-)

I think NM is doing a great job on my system. So I'd rather see a solution for sending sms through NM. :-) More and more computers comes with integrated 3g modem and just a slot for the simcard, so a sms service integrated in NM is going to be needed. :-)

Well, I actually got Wammu to work tonight, so I don't really need VMC anymore.

---

### Post by Rhubarb on 2010-01-03
If you're not using Network Manager to connect to the internet, empathy will by default refuse to go online.

This can be easily fixed by telling empathy not to rely on Network Manager for knowing the computer's online status:

[http://ubuntuforums.org/showthread.php?p=8537691#post8537691](http://ubuntuforums.org/showthread.php?p=8537691#post8537691)

---

### Post by alexfish on 2010-01-03
> **satriaulie said:**
> I'm sorry, but I don't really think you understand the problem.

First of all I'm in Norway.
I use Netcom, not Vodafone. Vodafone is just the name of the program.
Sms is working perfectly in the mentioned Vodafone program.

Anyway the problem is Network Manager and DBus.

Hi

Well that Clarifies The Question : Your not On Vodafone :


  Some info here for your Reading

[SIZE=2][COLOR=Blue][Vodafone Mobile Connect Software]("http://www.pcurtis.com/ubuntu-mobile.htm#vmc")

[COLOR=Black][SIZE=1]the device type listing are important with some of these devices > reason if the mode switching is not correct then the wrong Ports can be used  : Please Read all of the article Mentioned ![/SIZE][/COLOR]
[/COLOR][/SIZE]

---

