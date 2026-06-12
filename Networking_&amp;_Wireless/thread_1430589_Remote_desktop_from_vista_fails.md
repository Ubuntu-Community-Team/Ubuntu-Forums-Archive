---
title: "Remote desktop from vista fails"
date: 2010-03-15
forum: Networking &amp; Wireless
---

### Post by windyweather on 2010-03-15
I want to connect from Vista x86 to Ubuntu 9.10 Karmic - fully updated as of this date.
Using the preference I enabled Remote Desktop using a password and not requiring confirmation.

From Vista x86 I tried TightVNC and UltraVNC and got the same behaviour.

[http://www.uvnc.com/download/1082/1082viewer.html](http://www.uvnc.com/download/1082/1082viewer.html)
[http://www.tightvnc.com/](http://www.tightvnc.com/) both stable release and beta release behavior the same.

Open Windows Firewall for program on vista system.
Network is local 100mbs Ethernet.

Connection works fine.
Password requested.
Screen refreshes once and shows correctly.
Cursor moves fine.
No screen updates occur after that.

If you shut down the connection and then start it again you see the windows [firefox for example] that you opened last time.

You see the remote cursor move, but no updates of the screen occurs.

Looks like an Ubuntu bug.

Has anyone gotten this to work?? Is there a client for Vista that works?

- Thanks
Windy

---

### Post by sebastianabate on 2010-03-15
> **windyweather said:**
> I want to connect from Vista x86 to Ubuntu 9.10 Karmic - fully updated as of this date.
Using the preference I enabled Remote Desktop using a password and not requiring confirmation.

From Vista x86 I tried TightVNC and UltraVNC and got the same behaviour.

[http://www.uvnc.com/download/1082/1082viewer.html](http://www.uvnc.com/download/1082/1082viewer.html)
[http://www.tightvnc.com/](http://www.tightvnc.com/) both stable release and beta release behavior the same.

Open Windows Firewall for program on vista system.
Network is local 100mbs Ethernet.

Connection works fine.
Password requested.
Screen refreshes once and shows correctly.
Cursor moves fine.
No screen updates occur after that.

If you shut down the connection and then start it again you see the windows [firefox for example] that you opened last time.

You see the remote cursor move, but no updates of the screen occurs.

Looks like an Ubuntu bug.

Has anyone gotten this to work?? Is there a client for Vista that works?

- Thanks
Windy

Is Compiz active? There is an known _[bug]("https://bugs.launchpad.net/ubuntu/+source/vino/+bug/353126")_ that prevents Vino to update the screen changes with compiz. You have two options, disable compiz, or disable the Xorg xdamage extension in Vino (go to gconf-editor and change the key "/desktop/gnome/remote_access/disable_xdamage" to true); the second option makes the image refresh very slow, because every pixel needs to be sent over the net, not only the change ones.

---

### Post by windyweather on 2010-03-15
Apparently Compiz is a 3D desktop effect extension?? Correct?

So, I don't think I have that installed. How do I check?

I do have some fancy effects enabled that are apparently 2D. When I move the windows around they sort of Wave back and forth like they are soft. I'll be happy to turn this off tho.

so:
(1) How do I know if I have COMPIZ enabled? And how to remove it if I do?

(2) Is this wavy windows effect part of COMPIZ or something else?

Thanks,
windy

---

### Post by sebastianabate on 2010-03-15
> **windyweather said:**
> Apparently Compiz is a 3D desktop effect extension?? Correct?

So, I don't think I have that installed. How do I check?

I do have some fancy effects enabled that are apparently 2D. When I move the windows around they sort of Wave back and forth like they are soft. I'll be happy to turn this off tho.

so:
(1) How do I know if I have COMPIZ enabled? And how to remove it if I do?

(2) Is this wavy windows effect part of COMPIZ or something else?

Thanks,
windy

Yes, you have compiz enabled, but if you don't trust in my word ;-) you can open
System->Preferences->Appearance, and if in the Visual Effects Tab you have checked Normal or Extra, you have Compiz running; to disable it select None in the same Tab and click on Close. Then try connecting with a vnc client and check if the problem is gone.

---

### Post by windyweather on 2010-03-15
Thanks very much. That fixed it.
Works great now. Didn't recognise COMPIZ with "visual effects". :)
- windy

---

