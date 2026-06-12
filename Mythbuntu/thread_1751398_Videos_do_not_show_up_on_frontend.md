---
title: "Videos do not show up on frontend"
date: 2011-05-06
forum: Mythbuntu
---

### Post by natomb on 2011-05-06
Hello,

I have the problem that my videos (other media I have not tried so far) does not show up on my frontend.

Here is my setup:

[U]Directory layout (all directories and files are world-readable and writeable)
[/U]/Multimedia/Filme
/Multimedia/Filme/Deutsch
/Multimedia/Filme/English

every directory contains some video files (avi, mpeg, mkv, ...)

The directory is mounted via NFS (files are located on a different machine, there is no squashing used). Thus, my network layout consists of three machines:

NFS server (holding video files)
Myth backend
Myth frontend


I have configured the following "storage" in the Myth backend:

Video: /Multimedia/Filme


On the frontend, I have tried the following combinations for the video storage:

Empty
/Multimedia/Filme
/Multimedia/Filme:/Multimedia/Filme/Deutsch


Yet, not a single video will be available in the frontend.


Please, can you advice me on how to fix / further troubleshoot?


BTW: I am using Mythbuntu 11.04 on both backend and frontend.


Kindest regards
  Bjoern

---

### Post by tgm4883 on 2011-05-06
> **natomb said:**
> Hello,

I have the problem that my videos (other media I have not tried so far) does not show up on my frontend.

Here is my setup:

[U]Directory layout (all directories and files are world-readable and writeable)
[/U]/Multimedia/Filme
/Multimedia/Filme/Deutsch
/Multimedia/Filme/English

every directory contains some video files (avi, mpeg, mkv, ...)

The directory is mounted via NFS (files are located on a different machine, there is no squashing used). Thus, my network layout consists of three machines:

NFS server (holding video files)
Myth backend
Myth frontend


I have configured the following "storage" in the Myth backend:

Video: /Multimedia/Filme


On the frontend, I have tried the following combinations for the video storage:

Empty
/Multimedia/Filme
/Multimedia/Filme:/Multimedia/Filme/Deutsch


Yet, not a single video will be available in the frontend.


Please, can you advice me on how to fix / further troubleshoot?


BTW: I am using Mythbuntu 11.04 on both backend and frontend.


Kindest regards
  Bjoern

In the frontend in MythVideo, did you hit M and scan for changes?

---

### Post by natomb on 2011-05-07
Hi,


thank you for the hint. It worked.

Do I have to always press "M" and refresh the databases? Or is there a way to do this automatically? A cron job would do fine, I think.

---

### Post by tgm4883 on 2011-05-07
> **natomb said:**
> Hi,


thank you for the hint. It worked.

Do I have to always press "M" and refresh the databases? Or is there a way to do this automatically? A cron job would do fine, I think.

IIRC it does this automatically in 0.24, but it's a cron job that runs daily.

---

