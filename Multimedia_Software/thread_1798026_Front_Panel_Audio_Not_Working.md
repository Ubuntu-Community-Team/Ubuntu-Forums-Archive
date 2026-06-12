---
title: "Front Panel Audio Not Working"
date: 2011-07-05
forum: Multimedia Software
---

### Post by jdorenbush on 2011-07-05
After a recent hardware upgrade, I'm no longer able to use the front panel audio ports on my Antec P180 case. They worked fine before with my old ASUS motherboard, but with my new MSI 870-G45 motherboard I can't get them to work for some reason.

I checked out this thread, [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) but didn't see much in the way of problems/solutions with front panel audio ports, but it's a lengthy thread so maybe I missed it. :confused:

Any suggestions?

---

### Post by gordintoronto on 2011-07-05
With your old motherboard, the front panel ports were plugged in somewhere. When you installed the new motherboard, did you also plug the ports in?

What version of Ubuntu?

---

### Post by jdorenbush on 2011-07-05
Yea, I plugged all the connectors into the new mobo. And I've double checked them a few times, so I'm about 99% sure that isn't the problem.

I'm on a 64bit install of Ubuntu 11.04.

---

### Post by lidex on 2011-07-06
Try toggling the front panel audio connectors in the bios. Typical values are AC '97 and HD Audio.

---

### Post by jdorenbush on 2011-07-06
> **lidex said:**
> Try toggling the front panel audio connectors in the bios. Typical values are AC '97 and HD Audio.

The only thing I saw was the option to "Enable" or "Disable" an "HD Audio Controller". I tried disabling, but when I logged into Ubuntu and checked my Sound Preferences there was no hardware listed, so disabling it causes me to lose sound completely.

---

### Post by lidex on 2011-07-06
> **jdorenbush said:**
> The only thing I saw was "Enable" or "Disable" for HD Audio. Nothing about AC '97.
Try disabling then.

---

### Post by jdorenbush on 2011-07-06
> **lidex said:**
> Try disabling then.

Must have just missed my edit to the post above. ;)

Disabling that option caused all my sound to disable.

---

### Post by lidex on 2011-07-06
That's your onboard audio then. Should be another option for the front panel connectors.

---

### Post by jdorenbush on 2011-07-06
Maybe I'm overlooking something or just not looking in the right place because I can't seem to find anything about front panel connectors.

On MSI's website you can download the manual which contains screenshots of the menu choices in the BIOS.

[http://www.msi.com/product/mb/870-G45.html#?div=Manual](http://www.msi.com/product/mb/870-G45.html#?div=Manual)

Maybe you can look at my choices in the BIOS and direct me in the correct path? Thanks for your help!

FYI: My BIOS is A7599AMS V. 10.7 12142010

---

### Post by gordintoronto on 2011-07-06
Enable the audio. Are you using Unity or Gnome? With the audio enabled and earphones plugged in, Preferences/Sound, in the output tab, should offer a "connector" which uses the front jacks.

---

### Post by jdorenbush on 2011-07-07
> **gordintoronto said:**
> Enable the audio. Are you using Unity or Gnome? With the audio enabled and earphones plugged in, Preferences/Sound, in the output tab, should offer a "connector" which uses the front jacks.

I'm using Gnome. 

I see "Analog Output" and "Analog Headphones". The "Analog Headphones" option provides no sound.

---

### Post by gordintoronto on 2011-07-07
I'm more convinced than ever that it is a cabling problem.

---

### Post by jdorenbush on 2011-07-07
> **gordintoronto said:**
> I'm more convinced than ever that it is a cabling problem.

I plugged the connector, which only fits one way, into the "JAUD1" pins on my motherboard.

---

### Post by phoinx on 2011-09-14
How this story ends?

I have the same issue here, with same context (Gnome, "Analog Output" and "Analog Headphones" on Sound Preferences: Output...).

---

### Post by jdorenbush on 2011-09-14
> **phoinx said:**
> How this story ends?

Yea, I've pretty much given up on this. I'm not sure how to resolve the issue. :(

---

