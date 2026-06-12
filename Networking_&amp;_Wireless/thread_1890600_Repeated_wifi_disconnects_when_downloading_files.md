---
title: "Repeated wifi disconnects when downloading files?"
date: 2011-12-03
forum: Networking &amp; Wireless
---

### Post by rectec794613 on 2011-12-03
Hello. I keep getting disconnected from my wifi network whenever I'm downloading something. (Either HTTP, TCP, or UDP, I haven't downloaded files with any other protocol.) When I get disconnected, the network plasmoid says it's configuring the network, but this will go on forever. Sometimes it even says it's waiting for authorization, even though I already gave it my passkey. So I have to disable networking and wireless and re-enable them to reconnect. The disconnects happen at random, and can occur between a few seconds to 10 minutes in interval. I have the cursed RT2800PCI network module, which is naturally faulty, but I haven't had this problem until recently. Any suggestions? I feel like I should add some more info, so feel free to ask questions.

---

### Post by rectec794613 on 2011-12-18
Anybody? I think I've been fairly patient.

---

### Post by inobe on 2011-12-18
have you attempted normal troubleshooting?

cleared recent connections.

checked router settings.

picked up system updates updates along with kde upgrades.

what is the your kubuntu version?

---

### Post by rectec794613 on 2011-12-19
Thanks for responding. I don't have this problem on Windows, so it only seems to occur on Linux-based operating systems. (Very sure it's the aforementioned network module.) I get this problem with both KDE and GNOME, with their respective network applets. I also get it on fresh Ubuntu installs, and fresh DE installs. That said, I'm sure it doesn't have anything to do with connection history, but it wouldn't hurt to try. Can I get some further instruction if you're positive about this? Also, what specific router settings are you talking about? I don't think I've changed anything recently. I'm using GNOME-Shell as my main DE as of now. I am up-to-date as far as I can tell. 

Here's some version info: [LIST]
[*]Ubuntu 11.10
[*]network-manager version 0.9.1.90
[*]network-manager-applet version 0.9.1.90
[*]networkmanagement version 0.9
[*]gnome-shell version 3.2.1
[*]KDE version 4.7.2
[/LIST]

---

### Post by rectec794613 on 2011-12-25
Hello? Anybody?

---

### Post by Naggobot on 2011-12-25
I am also experiencing occasional partial disconnects. Symptom is that superficially the network seems connected but no data can be transferred through connection. There are even no errors in the system logs. 

For me the problem started after changing router and protocol from web to wpa-psk. I suspect that in my case the issue is with the wpa-psk enryption. Since the error is only occasional I have not yet tried downgrading to web. 

I am absolutely 100% sure that your problem and mine are totally separate problems but few years ago these wifi disconnects were a common occurrence if judged by the forum entries. At the time there was no solutions available or at least I did not see any real solutions offered. 

How ever I have never suffered from these disconnects until changing to wpa-psk and now I have them on two separate laptops with different hardware. 

So as an idea try wep instead of wpa-psk or some other more complicated encryption. It is more than likely that it will not have any effect but at least it will rule out one thing. 

Good luck.

---

