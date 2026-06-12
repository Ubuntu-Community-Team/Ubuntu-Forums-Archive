---
title: "Logitech Speaker Lapdesk N700 volume range"
date: 2010-08-24
forum: Multimedia Software
---

### Post by avion on 2010-08-24
I am on 10.04.1 with kernel 2.6.32-24 and using the Logitech N700 speaker lapdesk. The problem I am running into is that when the audio is sent to this device there are only 3 volume levels: 100%, 48%, and 0%. I confirmed these number by looking at the volume levels displayed by alsamixer.  Is there a way to tell alsa that there should be a wider range of volume levels?

---

### Post by lidex on 2010-08-28
Scroll to the section "Volume range anomalies" here:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

---

### Post by avion on 2010-08-28
> **lidex said:**
> Scroll to the section "Volume range anomalies" here:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

Excellent. This solution works perfectly.

lidex, many thanks!

---

### Post by jennkhutch on 2010-12-23
Reviving a thread because I am having this exact issue.  I checked out the link about volume range anomalies but I am not sure how to do what it says to do.  I'm still learning and I still don't grasp basic tasks. For example, where it say:

"You can either edit /etc/pulse/default.pa (you'll have to be root to do that) to change the behavior for all users, or copy that file to ~/.pulse/default.pa and then edit that file, to change behavior for the current user only.

Open the file mentioned above."

How exactly do I open/copy/edit that file from the terminal?

Thank you.

---

### Post by avion on 2010-12-24
> **jennkhutch said:**
> Reviving a thread because I am having this exact issue.  I checked out the link about volume range anomalies but I am not sure how to do what it says to do.  I'm still learning and I still don't grasp basic tasks. For example, where it say:

"You can either edit /etc/pulse/default.pa (you'll have to be root to do that) to change the behavior for all users, or copy that file to ~/.pulse/default.pa and then edit that file, to change behavior for the current user only.

Open the file mentioned above."

How exactly do I open/copy/edit that file from the terminal?

Thank you.

I think this is a pretty good tutorial/introduction to the Unix/Linux command line:

[http://info.ee.surrey.ac.uk/Teaching/Unix/](http://info.ee.surrey.ac.uk/Teaching/Unix/)

---

### Post by lidex on 2010-12-24
@jennkhutch
Specifically, open the file for editing thusly:
```
gksudo gedit /etc/pulse/default.pa
```
Make your changes, save, close, logout.

---

