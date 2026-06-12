---
title: "On board sound versus PCI card"
date: 2006-07-28
forum: Multimedia &amp; Video
---

### Post by jc750kwak on 2006-07-28
Okay

I am so happy with my first install of Ubuntu I could cry ..... but there is one niggle

I upgraded my PC with a new motherboard that has onboard sound (Via 82C686A/B chipset) but I also have a Soundblaster Pro2 PCI card in there

The system uses different sound devices on different boot ups. Sometimes it is the onboard Via, others it is the SB2. Have checked /etc/modules and that only shows sbp2

So my question is how can I configure Ubuntu to only load the SB2 ?

My reason? To stop having to reach behind the PC and swap the speaker cable between the outputs !

If I can't solve this I'm gonna have to invest in another Y audio cable and hook both outputs up to a switcher box I have lying around in a box somewhere

Yours hopefully

John

---

### Post by cacharreo on 2006-07-28
You must disable the onboard sound card from bios. In this way ubuntu only will work with the SB2

---

### Post by jc750kwak on 2006-07-29
Brilliant ! Worked flawlessly. Thanks  :)

---

