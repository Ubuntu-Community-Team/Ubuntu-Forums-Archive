---
title: "It's Official: Mac Trojan on the Loose... macOS redesign allows loopholes."
date: 2008-06-22
forum: Mac OSX
---

### Post by madjr on 2008-06-22
*"According to SecureMac, the Trojan horse runs hidden on the system, and allows a malicious user complete remote access to it. **The malware can send system and user [COLOR="DarkOrange"]passwords[/COLOR]**, and can avoid detection by opening ports in the firewall and turning off system logging. Even worse, **the AppleScript.THT Trojan horse can [COLOR="DarkOrange"]log keystrokes[/COLOR], [COLOR="Purple"]take pictures with your Mac's built-in iSight camera[/COLOR], take screenshots of whatever you are doing at a given moment, and even turn on file sharing, exposing your personal life even more.**"*



[http://news.softpedia.com/news/It-039-s-Official-Mac-Trojan-on-the-Loose-88472.shtml](http://news.softpedia.com/news/It-039-s-Official-Mac-Trojan-on-the-Loose-88472.shtml)

the guy in the comments is right:

*"**freebsd does not allow viruses. mac os redesign allows loopholes**, i guess **[COLOR="DarkOrange"]they are getting a % from the antivirus companies[/COLOR]. its a big business**. I just downloaded **ubuntu for PPC** and i'll be getting rid of macos for good and the not-direclty affiliated (in quotes) antivir companies. Lusers, educate yourselfs."*

---

### Post by days_of_ruin on 2008-06-22
Thats what happens when you try to be too noob friendly.

---

### Post by cardinals_fan on 2008-06-22
> **days_of_ruin said:**
> Thats what happens when you try to be too noob friendly.
Very true.

---

### Post by jrusso2 on 2008-06-22
It says in the article

However, the user must download and open the Trojan horse in order to become infected. It moves itself immediately to the /Library/Caches/ folder and adds itself to the System Login Items, according to SecureMac. This is where the company's MacScan 2.5.2 comes in and saves the day. MacScan detects, isolates, and removes spyware like applications, such as keystroke loggers and Trojan horses, to protect your Mac.

---

### Post by cardinals_fan on 2008-06-22
> **jrusso2 said:**
> It says in the article

However, the user must download and open the Trojan horse in order to become infected. It moves itself immediately to the /Library/Caches/ folder and adds itself to the System Login Items, according to SecureMac. This is where the company's MacScan 2.5.2 comes in and saves the day. MacScan detects, isolates, and removes spyware like applications, such as keystroke loggers and Trojan horses, to protect your Mac.
As I expected.  Only idiots get infected.

---

### Post by Woormy on 2008-06-22
> **cardinals_fan said:**
> As I expected.  Only idiots get infected.

I have run Windows machines for years at a stretch without protection or incidents. Seriously, viruses, trojans, etc. are things people install themselves.

---

### Post by days_of_ruin on 2008-06-22
No root password required of course.Just need people who shouldn't be
using a computer.

---

### Post by cardinals_fan on 2008-06-22
> **woormy said:**
> i Have Run Windows Machines For Years At A Stretch Without Protection Or Incidents. Seriously, Viruses, Trojans, Etc. Are Things People Install Themselves.
+1

---

### Post by Iandefor on 2008-06-23
> **madjr said:**
> the guy in the comments is right:

*"**freebsd does not allow viruses. mac os redesign allows loopholes**, i guess **[COLOR=DarkOrange]they are getting a % from the antivirus companies[/COLOR]. its a big business**. I just downloaded **ubuntu for PPC** and i'll be getting rid of macos for good and the not-direclty affiliated (in quotes) antivir companies. Lusers, educate yourselfs."*No, he's not. FreeBSD suffers from remotely-exploitable security holes. Visit the [freebsd-security-notifications-list archives]("http://lists.freebsd.org/pipermail/freebsd-security-notifications/"). They seem to average two a month this year.

NetBSD suffers from them. OpenBSD suffers from them; even at the most optimistic estimate provided by the OpenBSD project, they've had two in the default install in the last thirteen years. *Everything* plugged into a network runs the risk of being exploited. Whether or not it *will* be exploited by a virus is a distinct question from whether or not it *can*. Saying "FreeBSD does not allow viruses" just because nobody has bothered to do so yet is just ignorant.

Yes, it would probably prove a harder target to completely trash than OS X, since OS X is made up of a lot more software than just FreeBSD, and the only sure common denominator for FreeBSD systems is the ~45 MiB "base" distribution, but that's beside the point.

---

### Post by 3rdalbum on 2008-06-25
I don't believe that this trojan exists.

Yes, trojans for Mac OS X really do exist, and they are certainly possible. But I think this whole article is just an attempt to get Mac users to buy the company's anti-virus program.

Some parts of the article are quite unrealistic - evading detection by opening ports in the firewall? How exactly does that help the virus evade detection? OS X's firewall is leaky already, but any user looking in firewall configuration will see unexpected ports open.

There doesn't seem to be any serious analysis of this trojan, either - "Oh, we found people talking about it on a hacker website". Yeah right. Why does it get distributed with a cryptic filename ("ASthtv05"), when every trojan I've heard of gets distributed with an enticing name like "setup.exe" or "Photo of me.jpg.com".

I'm not a conspiracy theorist who claims that anti-virus companies actually write viruses, but I do think that those three anti-virus companies are committing a hoax to try and spark sales of their white elephant.

---

### Post by cardinals_fan on 2008-06-25
> **3rdalbum said:**
> I don't believe that this trojan exists.

Yes, trojans for Mac OS X really do exist, and they are certainly possible. But I think this whole article is just an attempt to get Mac users to buy the company's anti-virus program.

Some parts of the article are quite unrealistic - evading detection by opening ports in the firewall? How exactly does that help the virus evade detection? OS X's firewall is leaky already, but **any user looking in firewall configuration will see unexpected ports open**.

There doesn't seem to be any serious analysis of this trojan, either - "Oh, we found people talking about it on a hacker website". Yeah right. Why does it get distributed with a cryptic filename ("ASthtv05"), when every trojan I've heard of gets distributed with an enticing name like "setup.exe" or "Photo of me.jpg.com".

I'm not a conspiracy theorist who claims that anti-virus companies actually write viruses, but I do think that those three anti-virus companies are committing a hoax to try and spark sales of their white elephant.
Do you honestly think that any "average" user is going to be looking through their firewall config?

With that said, I have long considered antivirus software to be a scam.  Foolish decisions by the **user** cause 99.9% of infections.

---

### Post by LaRoza on 2008-06-25
> **cardinals_fan said:**
> 
With that said, I have long considered antivirus software to be a scam.  Foolish decisions by the **user** cause 99.9% of infections.

I believe that also, when it is applied to non servers.

Someone with a computer and anti-virus software but with no education on using a computer had a lot of virus issues.

After I got done with this person (only a matter of minutes), they now follow my advise to a letter and have a perfectly secure Windows with no antivirus or virus infections.

---

### Post by AlphaMack on 2008-06-25
Uhm, this is very real.

[MacNN Thread on ARDAgent](http://forums.macnn.com/90/mac-os-x/370693/huge-crazy-ridiculous-os-x-security/)

Apple has allowed this to run as root by default with no authentication necessary.  Might as well run the entire system 777.

---

### Post by nerd0795 on 2008-06-28
Uh oh, and I'm thinking about buying a mac, and now since I want one all of this **** happens.  Whatever, I love removing viruses :popcorn::popcorn::popcorn:

and I know how to browser the internet safely :)

---

