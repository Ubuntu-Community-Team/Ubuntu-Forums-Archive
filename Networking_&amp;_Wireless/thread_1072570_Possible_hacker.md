---
title: "Possible hacker?"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by Excedio on 2009-02-17
Hey Guys

Was at work today with my fiancee's laptop that runs Freespire Linux. I went to change my Pandora station when i see that someone is trying to remotely access the laptop.

This is the IP that was trying to get in:

73.18.18.72.static.tierzero.net

Does anybody recognize this? Has anyone else experienced this? Here is the information regarding the Host *static.tierzero.net

[http://www.robtex.com/dns/static.tierzero.net.html]("http://www.robtex.com/dns/static.tierzero.net.html")

Here is the results of a reverse IP address lookup:
[QUOTE=Zoneedit.com]Comcast IP Services, L.L.C. CABLE-1 (NET-73-0-0-0-1) 
                                  73.0.0.0 - 73.255.255.255
Comcast IP Services, L.L.C. NAPLES-CDM-1 (NET-73-18-0-0-1) 
                                  73.18.0.0 - 73.18.255.255[/QUOTE]Comcast IP Services, L.L.C. CABLE-1 (NET-73-0-0-0-1) 
                                  73.0.0.0 - 73.255.255.255
Comcast IP Services, L.L.C. NAPLES-CDM-1 (NET-73-18-0-0-1) 
                                  73.18.0.0 - 73.18.255.255

[QUOTE=http://www.ipaddresser.com/reverse.php/73.18-0]City / Region / Company: Mount Laurel
Country: United States
Map: [View]("http://maps.google.com/maps?f=q&hl=en&z=7&q=40,-75")[/QUOTE]


FYI...I did block its access to the laptop.

---

### Post by punx45 on 2009-02-17
what do you mean by assess the computer?   did you find this in a log? which one?

---

### Post by Excedio on 2009-02-17
> **punx45 said:**
> what do you mean by assess the computer?
My bad...fixed the typo...supposed to be access.



> **punx45 said:**
> did you find this in a log? which one?
I knew because the laptop's remote desktop is set to notify the laptop user that someone is trying to gain access, and asks if that remote user can gain access.

---

### Post by Ketara on 2009-02-17
This used to happen to me at work a lot too. I never figured out who was doing it, but changing the remote desktop settings to never allow anybody access will get rid of the popups at least.

---

### Post by Excedio on 2009-02-17
> **Ketara said:**
> This used to happen to me at work a lot too. I never figured out who was doing it, but changing the remote desktop settings to never allow anybody access will get rid of the popups at least.

I'm not terribly worried about anyone breaking in since I would have to allow it. Not to mention that I have a crazy *** password. I'm more just curious if anyone else has been seeing this or know whom it is. Thanks.

---

### Post by Ketara on 2009-02-17
My work is right next to a college campus, so I always figured it was some student playing with computers and seeing what all he could do. It never really worried me, was just sort of annoying.

I'd be surprised if whoever is doing this in your case has a malicious intent. 'Course, I don't know where you work so I could be wrong!

---

### Post by Excedio on 2009-02-17
I work in clearwater florida, but the IP address is from the philly area...

---

### Post by punx45 on 2009-02-17
its probably not any one particular individual singling you out.   it is probably someones hijacked PC that is part of a botnet swarm probing for computers with vulnerabilities.   i get activity like that from all over the place (including the Department of Defense *tinfoil hat*) on my webserver and ssh.   if you dont use remote desktop, might as well just disable it to end the annoyances.

---

