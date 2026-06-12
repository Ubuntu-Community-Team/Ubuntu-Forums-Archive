---
title: "Chrome as default web browser"
date: 2011-04-18
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by el_sordo on 2011-04-18
Anyone know how to set Chrome as the preferred web browser in gnome-default-applications-properties? I think there was a 'Custom' option in Maverick.

Thanks.

---

### Post by VMC on 2011-04-18
As soon as I start Chrome, it asks me if I want to make it default.

Also in Chrome under "Preferences > Basics > Default Browser", you can choose.

---

### Post by Harry33 on 2011-04-18
> **el_sordo said:**
> Anyone know how to set Chrome as the preferred web browser in gnome-default-applications-properties? I think there was a 'Custom' option in Maverick.
Thanks.

Above VMC described how it is done.

You can also set Chromium as a preferred application in Gnome by going to:
System => Preferences => Preferred applications
And from there choose tab "Internet" and field "Web Browser".
From there, choose "Chromium Web Browser".

---

### Post by el_sordo on 2011-04-18
I set Chrome as the default browser in Chrome's preferences, but hyperlinks in Evolution still open Firefox. Plus the 'Preferred Applications' still indicate Firefox as being the default.  I don't use the Chromium package...I use Google's .deb package. Tried logging out, restarting Evolution, Chrome, etc...

---

### Post by Harry33 on 2011-04-18
> **el_sordo said:**
> I set Chrome as the default browser in Chrome's preferences, but hyperlinks in Evolution still open Firefox. Plus the 'Preferred Applications' still indicate Firefox as being the default.  I don't use the Chromium package...I use Google's .deb package. Tried logging out, restarting Evolution, Chrome, etc...

There you have an answer, you cannot set Google Chrome to fully support Ubuntu's Gnome applications.
You are adviced to use Chromium from Natty official repos or even to use PPA's like beta channel. These will fully support Ubuntu's Gnome.

---

### Post by el_sordo on 2011-04-18
> **Harry33 said:**
> There you have an answer, you cannot set Google Chrome to fully support Ubuntu's Gnome applications.
You are adviced to use Chromium from Natty official repos or even to use PPA's like beta channel. These will fully support Ubuntu's Gnome.

I installed the chromium-browser package and it's still not showing up in 'Preferred Applications'. It's also not showing up in the dash. Had to use 'Alt-F2' to get it in the launcher.

---

### Post by prusis on 2011-04-18
> **Harry33 said:**
> There you have an answer, you cannot set Google Chrome to fully support Ubuntu's Gnome applications.
You are adviced to use Chromium from Natty official repos or even to use PPA's like beta channel. These will fully support Ubuntu's Gnome.

Are you saying that it will not be possible to set Chrome as default in Natty? Or is just in beta? Because in Maverick Chrome worked as default very well (for instance any links from Skype etc.)

---

### Post by el_sordo on 2011-04-18
This could be related to [LP: #670128]("https://bugs.launchpad.net/ubuntu/+source/chromium-browser/+bug/670128"), however, I have chromium-browser 10.0.648.205~r81283-0ubuntu1 installed which the changelog indicates 670128 was fixed.

---

### Post by jon4248 on 2011-04-18
install chrome, remove Firefox. done. hehe..j/k :P

---

### Post by beejee on 2011-04-23
I had the same thing but than I noticed that ~/.local/share/applications/mimeapps.list did't exist only an empty mimeapps.list.new (fresh natty beta install from last week)

After making an empty mimeapps.list chrome made itself default without any problems.

---

### Post by screaminj3sus on 2011-04-23
> **Harry33 said:**
> There you have an answer, you cannot set Google Chrome to fully support Ubuntu's Gnome applications.
You are adviced to use Chromium from Natty official repos or even to use PPA's like beta channel. These will fully support Ubuntu's Gnome.

Yeah it seems to just be an issue with official chrome stable. I am using google's official chrome dev repo and setting chrome as default works system wide.

---

### Post by ninjaaron on 2011-04-23
the only problem with making Chrome your default browser is that, well, you know, then Chrome is your default browser... which is tragic in and of itself. :P

---

### Post by lancest on 2011-04-23
I prefer using Chromium.
However have fund it buggy on 11.04.
[LIST=1]
[*]Sometimes crashes while using Flash.
[*]Problems with attaching files in email. (freezing at inopportune time)
[/LIST]

Too buggy! Where's the updates Google?
Using Firefox more because I can trust it.

---

### Post by Harry33 on 2011-04-23
> **lancest said:**
> I prefer using Chromium.
However have fund it buggy on 11.04.
[LIST=1]
[*]Sometimes crashes while using Flash.
[*]Problems with attaching files in email. (freezing at inopportune time)
[/LIST]

Too buggy! Where's the updates Google?
Using Firefox more because I can trust it.

Do you use 32-bit setup here?
I have also experienced freezing on my 32-bit setup, but never on my 64-bit setup.

---

### Post by beew on 2011-04-23
No way, Firefox is way better.

---

### Post by lancest on 2011-04-23
> **Harry33 said:**
> Do you use 32-bit setup here?
I have also experienced freezing on my 32-bit setup, but never on my 64-bit setup.

Using 64 bit.

---

### Post by lancest on 2011-04-23
You know I failed to consider some variables.

[LIST]
[*]11.04 is beta, so Chromium might be blameless
[*]And about battery computing performance.
[/LIST]
Chromium is currently performing alot better on DC than Firefox.
(smother scrolling, faster tab switching, handling load smoothly)

---

### Post by gwoodruff on 2011-04-23
I am running 64b Natty with Gnome3, use Chrome as my default browser and was able to set it as the default browser via preferred applications. It is faster then Firefox, I do not experience crashes and links from Evolution 3.0 open with Chrome. Now if I could find a ppa for Evolution 3.0 for Maverick on my IBM Thinkpad running Xubuntu I would be a happy camper!

---

