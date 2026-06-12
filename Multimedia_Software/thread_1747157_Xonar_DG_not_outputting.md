---
title: "Xonar DG not outputting"
date: 2011-05-02
forum: Multimedia Software
---

### Post by martin.burianjr on 2011-05-02
Hi all,
I've just brought a Asus Xonar DG and put it in my case - and found out that it's about the only card that is not easy to get working. I've updated my ALSA to  1.0.24 using [this]("http://ubuntuforums.org/showthread.php?t=1681577") how-to. Then I reinstalled pulse with all the utilities and got it to look like working, with one problem only: no sound is output.
I use Rythmbox for playback. In pavucontrol the bar below the soundcard output indicates that there's something playing, but no sound gets to my headphones. Has anyone encountered that? I've tried nearly all combinations of setting the output devices in various places like Sound settings and pavucontrol, but none worked.
Thanks in advance

---

### Post by igitur on 2011-05-03
Is the sound card detected at all? According to this bug, the support for the card is still coming:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/684920](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/684920)

---

### Post by martin.burianjr on 2011-05-03
Yes, it is detected, it's visible in pavucontrol, aslamixer and in the Sound settings. And I'm using 1.0.24 version of ALSA, said to cooperate with this card in the "[this]("http://ubuntuforums.org/showthread.php?t=1681577")" how-to  i linked above. Also some really weak clicking sound gets out when enabling the card.

---

### Post by Yellow Pasque on 2011-05-03
The Xonar DG worked for me after upgrading ALSA (but it does make a strange clicking noise when switching outputs). Can you run alsa-info script? [http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973](http://ubuntuforums.org/attachment.php?attachmentid=182689&d=1296839973)

---

### Post by martin.burianjr on 2011-05-03
It ain't a "strange clicking noise", it's just a barely audible click I was listening for.
The alsa-info is in the attachment, thanks for caring.

---

