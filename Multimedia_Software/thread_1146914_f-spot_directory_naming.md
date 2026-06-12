---
title: "f-spot directory naming"
date: 2009-05-03
forum: Multimedia Software
---

### Post by Cammy on 2009-05-03
I recently switched from Hardy to Jaunty (new machine) and noticed that f-spot has changed how it organizes the pics that I download from my Canon camera.

In Hardy, it created a very nice directory structure, with a folder for each year, and within that a folder for each month, and within that a folder for each day.  It was very easy to find things.

In Jaunty, it just uses a conglomerated directory name, sort of like this:

2009-03-29-1.36.01

Which is very annoying!!!

Anyone have any clue how to restore the old behaviour?

---

### Post by texasflyfisher on 2009-05-04
I wish in my case that at least it was creating directories. After I upgraded from 8.10 to 9.04, it now places all my newly important photos in my home directory rather than ~/Photos where it used to. I checked my Import Settings folder and it is Photos. Any ideas?

---

### Post by Cammy on 2009-05-04
> **texasflyfisher said:**
> I wish in my case that at least it was creating directories. After I upgraded from 8.10 to 9.04, it now places all my newly important photos in my home directory rather than ~/Photos where it used to. I checked my Import Settings folder and it is Photos. Any ideas?

Maybe it's a permissions thing.  Have you checked permissions on your photos folder?

---

### Post by texasflyfisher on 2009-05-04
> **Cammy said:**
> Maybe it's a permissions thing.  Have you checked permissions on your photos folder?

Doubtful. I can traverse to ~/Photos/2009 and create a directory in there. The perms look fine to me. Besides, I didn't re-install this machine, just upgraded it. I have another machine that I installed 9.04 from scratch and it has the same issue.

---

### Post by Cammy on 2009-05-04
Ahh, I was thinking that maybe you had rights but the app didn't.

I'm not sure what else to try, sorry!

---

### Post by texasflyfisher on 2009-05-05
> **Cammy said:**
> Ahh, I was thinking that maybe you had rights but the app didn't.

I'm not sure what else to try, sorry!

That's alright. Thanks for the help though. I appreciate.

I did find that others have the same problem I have and has been reported in [https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/354264](https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/354264) and I subscribed to it so hopefully it will be fixed soon or at least provide a workaround.

---

### Post by UncleLev on 2009-06-10
> **texasflyfisher said:**
> I wish in my case that at least it was creating directories. After I upgraded from 8.10 to 9.04, it now places all my newly important photos in my home directory rather than ~/Photos where it used to. I checked my Import Settings folder and it is Photos. Any ideas?

Same with me.

On 8.04, they would at least be placed in sub-directories of ~/Photos... On 9.04, f-spot doesn't create sub-directories for me, and instead just throws all the camera's images into whatever folder you select. This of course means, that every time I want to transfer pictures, I need to delete the ones I did before, rename them or move them. Since I typically format my camera's memory stick each time after transfering pics, the new ones being transfered always have the same file names as those I have already transfered, and since F-Spot isn't making directories this has become a rather annoying problem.

---

