---
title: "Mythbuntu 12.04 Dual Boot - advanced partitioning tool"
date: 2013-02-04
forum: Mythbuntu
---

### Post by *drew on 2013-02-04
I've spent many hours on this problem, so any help would be greatly appreciated.

I am trying to install Mythbuntu 12.04.1 alongside Mythbuntu 10.04.

When I tried this in Virtual Box, I got the dialog box shown in the attached
 screenshot (notice the small text with the link to the "advanced partitioning tool").

When I try the same operation on my real machine, I don't get the advanced option.

** Can anyone tell me what I need to do to get this option to appear? **

I am using the same live cd image in both cases (burnt to a disc for the real machine).
The test install in Virtual Box was successful - I could boot both OS's.

Virtual Box is running on my laptop with the following partition configuration for the test install:

```

[FONT=Courier New]sda1    /boot    (mythbunu 10.04)
sda2             (extended partition)
sda5    /        (mythbunu 10.04)
sda6             (target partition for mythbuntu 12.04)
sda3             (linux swap)
[/FONT]
```The real machine has the following partition configuration (sda5 and sda6 reversed):

```

sda1    /boot    (mythbunu 10.04)
sda2             (extended partition)
sda5             (target partition for mythbuntu 12.04)
sda6    /        (mythbunu 10.04)
sda3             (linux swap)

sdb1             (additional storage for videos)

```

---

