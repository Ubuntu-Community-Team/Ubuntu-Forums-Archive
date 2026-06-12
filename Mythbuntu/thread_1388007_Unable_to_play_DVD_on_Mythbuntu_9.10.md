---
title: "Unable to play DVD on Mythbuntu 9.10"
date: 2010-01-22
forum: Mythbuntu
---

### Post by mythbuntu101 on 2010-01-22
I'm unable to play DVD on Mythbuntu 9.10 . Can someone tell me the step by step configuration process to allow for playing DVDs?

---

### Post by myth1914 on 2010-01-22
Is there a specific application you are using?  

Assuming you're using the default Gnome desktop, the simple answer is

aptitude -y install libdvdcss2 libdvdnav ubuntu-restricted-extras

then play it with totem - or whatever the default movie player is these days.

---

### Post by angelsguitar on 2010-01-22
Probably you need to install the libdvdcss2 library, which is required to play encoded DVD's

Click on the Applications button, them System, and then select "Mythbuntu Control Centre".  Once there, click on the last button to the right, labeled "Proprietary Codecs".  Check the following options (you'll have to hit apply once for every one of them):
-Enable Medibuntu Proprietary Codec Support"
-Enable medibuntu GPG Keyring
-Enable libdvdcss2

Hope this helps.

---

### Post by myth1914 on 2010-01-22
My mistake, I missed the mythbuntu for some reason.  Angels guitar is accurate.  Enable the codecs in mythbuntu-control-centre  [URL="http://ubuntuforums.org/member.php?u=394880"]
[/URL]

---

### Post by Techmanm on 2010-01-26
Hello, i'm having the same problem.
I have enabled the codecs but when i play the DVD file i'm getting the message "change video renderer.

Can someone please tell me what to do.

---

### Post by mythbuntu101 on 2010-01-28
go to  synaptic and install libdvdcss2, restart and you should be ok

---

### Post by Techmanm on 2010-01-28
I went to synaptic, installed libdvdcss2 and restarted but i'm stil getting the same message. "video renderer has to be changed"

---

