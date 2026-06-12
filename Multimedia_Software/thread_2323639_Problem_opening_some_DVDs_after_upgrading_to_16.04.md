---
title: "Problem opening *some* DVDs after upgrading to 16.04"
date: 2016-05-06
forum: Multimedia Software
---

### Post by whitney4 on 2016-05-06
After upgrading to 16.04, I suddenly started experiencing problems opening *some* DVDs. Take, for instance, some of the recent DVDs that I have tried to open,  such as Buffy, Angel, and Boy Meets World season sets. These are all  legit, region 1 releases and in flawless condition. Importantly, 90% of  these discs still do open and play just fine. Only some of them do not. For  example, all of Boy Meets World Season 1 opened, as did discs 1 and 2 of  Season 2, but Season 2 Disc 3 will not. I took it from one computer to  another and had the same problem there. The type of disc, region, and whether CSS is present is static across both affected and un-affected discs. I can come up with no explanation for why most discs are loading and a select few are not.

 I'll preemptively answer some questions that I anticipate getting:

 - Yes, I have installed the restricted formats / libdvdcss. About 90-95% of DVDs play with no trouble.
 - I have tried purging and re-installing restricted formats /  libdvdcss, but continue getting the same problems for the affected  discs.
 - No, the DVDs are not physically unreadable or a different region; they worked fine before the upgrade and still do on non-Linux devices.
 - This affects multiple computers (different makes and models) and DVD drives (ditto), so it's not a hardware issue.
 - I have tried deleting /.dvdcss folder and rebooting, but that solves nothing (incidentally, the folder for the affects discs are empty, which is what leads me to think that this is libdvdcss-related).
 - The volume is loading as an unknown format according to Ubuntu's "Disks" application, so it is recognizing that a disc is present (and it correctly reads the size of the data on the disc).
 - Wine-based programs also seem to be reading the disc label just fine, but see no files present.
 - Most damning of all that this is libdvdcss-related, the DVDs are perfectly readable by MakeMKV, which I believe has its own decryption codecs.
 - This only started happening after I upgraded to 16.04, but it's possible that another software upgrade is the cause; I was only applying minimal updates to the computer that I was mainly using for DVDs (it was on 14.04 before).
 - The BMW discs in my example are not encrypted, but Bolt, for example, is encrypted and reads just fine, so it is not an encryption problem.

Anyone know what the problem might be? Or how to fix it?

---

