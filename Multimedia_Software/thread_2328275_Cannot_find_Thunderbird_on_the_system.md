---
title: "Cannot find Thunderbird on the system"
date: 2016-06-19
forum: Multimedia Software
---

### Post by wjbradley on 2016-06-19
Recently I installed Ubuntu 14.04 from a thumb drive on an HP tablet. The installation went through without a problem.
When I came to set up the internet on Thunderbird I could not find it. When I checked the installed software Thunderbird is listed as installed but I can't find it. :confused:
Any help would be appreciated.
Thank you.

---

### Post by deadflowr on 2016-06-19
If you have the mail envelope in the top panel (right-side)
Click it and it should show something like Mail.
Click on that and thunderbird should open.

---

### Post by vasa1 on 2016-06-19
> **wjbradley said:**
> Recently I installed Ubuntu 14.04 from a thumb drive on an HP tablet. The installation went through without a problem.
When I came to set up the internet on Thunderbird I could not find it. When I checked the installed software Thunderbird is listed as installed but I can't find it. :confused:
Any help would be appreciated.
Thank you.
Please post the output of *apt-cache policy thunderbird*
```
10:36 PM ~ $ apt-cache policy thunderbird
thunderbird:
  Installed: (none)
  Candidate: 1:38.8.0+build1-0ubuntu0.16.04.1
  Version table:
     1:38.8.0+build1-0ubuntu0.16.04.1 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 Packages
     1:38.6.0+build1-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
10:41 PM ~ $ 

```In my case, I don't have it installed. If you do, run
```
which thunderbird
```and post the output here or, if you like, just run the output of "which thunderbird" as a command by itself.

---

### Post by wjbradley on 2016-06-21
Thank you deadflowr, your solution solved it. When I opened the system, there was no envelope in the upper right as you suggested. There was a box on the left that searches and there was Thunderbird. I was able to open it. Then when I went to shut the system down, I noticed an envelope on the upper right, clicked on it and there was Thunderbird. Thank you for your help and all the others that answered my question. I don't know how to mark this solved.

---

### Post by vasa1 on 2016-06-21
> **wjbradley said:**
> ... I don't know how to mark this solved.
Here: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

