---
title: "Unsupported Codec For Output Stream #0.1 FLV to MPG WinFF"
date: 2008-05-19
forum: Multimedia Software
---

### Post by avkhatri on 2008-05-19
I installed winff and I wanted to convert video to my sansa e200 that is running rockbox. I have FLVs that I want to make into MPGs. I selected the correct outputs for what I want to conver to and all but when I hit convert a bunch of text scrolls up and it says Unsupported Codec For Output Stream #0.1. Here is an image of what it looks like. I can play mpeg files fine but for some reason I can't convert them from FLV

[IMG]http://img227.imageshack.us/img227/5044/screenshotee0.png[/IMG]

---

### Post by avkhatri on 2008-05-21
please does anyone have any ideas?

---

### Post by kostkon on 2008-05-21
Do you use the *FFMpeg* from the [*Medibuntu* repository]("http://medibuntu.org/")?

---

### Post by avkhatri on 2008-05-21
> **kostkon said:**
> Do you use the *FFMpeg* from the [*Medibuntu* repository]("http://medibuntu.org/")?

No I am not using FFMpeg from the medibuntu repository. I will try that, but since I use winff which the the graphical version of FFMpeg will I be able to use WinFF after using the medibuntu repository?

EDIT: I get the repository and when i update apt-get I get this:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

EDIT: Ok it works and I can convert the mpegs now :), thanks.

---

### Post by FakeOutdoorsman on 2008-05-21
[Adding the Medibuntu Repositories]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f") details the GPG key instructions.

---

