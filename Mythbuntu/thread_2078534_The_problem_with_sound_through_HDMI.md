---
title: "The problem with sound through HDMI"
date: 2012-10-31
forum: Mythbuntu
---

### Post by ogogon on 2012-10-31
Good day!
I have a problem with sound through HDMI.

I use a video card Inno3D GF-GT440-DVI-VGA-HDMI-SDDR3-1GB and monitor Benq M2700HD. They are connected with an HDMI cable.

I install Mythbuntu from mythbuntu-12.04.1-desktop-amd64.iso
Initially, I used the default video driver. However, when viewing the video image moved by some waves.
Then I installed the proprietary driver and the video quality has improved.

Unfortunately I was not able to achieve what would output sound in monitor's speaker system  via HDMI.

I went through all of the proposed Mythtv sound settings, where mentioned HDMI. Unfortunately, when you run on the test, sound does not appear.

[B]What do I need to do, what would Mythbuntu began to be used as sound device a built-in speakers on HDMI monitor?
[/B] 
Ogogon.

---

### Post by nickrout on 2012-10-31
> **ogogon said:**
> Good day!
I have a problem with sound through HDMI.

I use a video card Inno3D GF-GT440-DVI-VGA-HDMI-SDDR3-1GB and monitor Benq M2700HD. They are connected with an HDMI cable.

I install Mythbuntu from mythbuntu-12.04.1-desktop-amd64.iso
Initially, I used the default video driver. However, when viewing the video image moved by some waves.
Then I installed the proprietary driver and the video quality has improved.

Unfortunately I was not able to achieve what would output sound in monitor's speaker system  via HDMI.

I went through all of the proposed Mythtv sound settings, where mentioned HDMI. Unfortunately, when you run on the test, sound does not appear.

[B]What do I need to do, what would Mythbuntu began to be used as sound device a built-in speakers on HDMI monitor?
[/B] 
Ogogon.

Are you sure your monitor supports sound over HDMI? I know TVs do, but I have never used an hdmi monitor.

Other than that, go into the Setup Wizard and it will scan your audio devices, and there is a built in speaker test.

---

### Post by ogogon on 2012-10-31
[QUOTE=nickrout]Are you sure your monitor supports sound over HDMI? I know TVs do, but I have never used an hdmi monitor.[/QUOTE]
This monitor has two HDMI inputs.
To the other input connected mediapalyer G-mini MagicBox HDR1100H. He successfully reproduces sound through HDMI.

[QUOTE=nickrout]Other than that, go into the Setup Wizard and it will scan your audio devices, and there is a built in speaker test.[/QUOTE]
I already did, and no result.
None of the modes, where HDMI, audio is not yet appeared.

Ogogon.

---

### Post by ertyu on 2012-11-13
I found that I have to have the HDMI monitor connected at bootup on my GT430 to have sound work. Otherwise alsa doesn't detect the modes it supports and won't send any sound.

---

