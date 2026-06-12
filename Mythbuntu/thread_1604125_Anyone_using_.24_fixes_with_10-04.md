---
title: "Anyone using .24 fixes with 10-04?"
date: 2010-10-23
forum: Mythbuntu
---

### Post by williammanda on 2010-10-23
Is anyone using .24 fixes with any ubuntu 10-04? If so, would you please give feedback.
Thanks

---

### Post by williammanda on 2010-10-23
I noticed what appears to be that ripping DVDs has been removed:

Remove MTD (myth transcoding daemon) and therefore the ability to directly rip DVDs ([25874], [25876]) 

Is this true?

---

### Post by tgm4883 on 2010-10-23
Yes it is.

---

### Post by andree_b on 2010-10-25
What's the reasoning for that?

---

### Post by tgm4883 on 2010-10-25
> **andree_b said:**
> What's the reasoning for that?

That's a question for upstream, but IIRC the reason for that is because storage groups are taking over the job of local frontend storage and the local frontend can't write a file to a storage group.

---

### Post by azmyth on 2010-10-25
I was using it but had to downgrade since there are seek table issues with PVRx50s and MPEG streams thus I couldn't FF or rewind.

---

### Post by jbman on 2010-10-26
couple of days using it with my 10.04 box

I had some issues with playback after a pause, i deleted my audio settings and chose a different option rather than /dev/adsp and all working well.

other than a few quirks with screens etc, all seems to be working quite well.

---

### Post by joshoekstra on 2010-10-27
Using it for a couple of weeks as an aid in translation and need to say it's really nice once you work the kinks out(should be worked out now thanks to the mythbuntu team :))
BTW I'm using PVRxx0's and didn't have any trouble with seektables or the like, sure it's a bug in .24?

---

### Post by azmyth on 2010-10-28
I saw there was bug fix for this issue in 0.23 so since I'm compiling 0.24 I looked at the code and saw the patch was in there yet I have the issue. I was using 0.24 and had the issue and then I downgraded and the issue went away. I don't know. It's strange that I would have it (no ff and no watch recording thumbnails) and you don't.

---

