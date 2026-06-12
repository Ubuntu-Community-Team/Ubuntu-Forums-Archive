---
title: "Slack and black screen after launch"
date: 2022-05-28
forum: Multimedia Software
---

### Post by bayberry on 2022-05-28
Hello everyone,

I have problem with Slack application, I installed it and after launch it's shows black screen.

Does anyone have similar problem with Slack on Ubuntu 22.04 LTS?

Thanks in advance!

---

### Post by #&amp;thj^% on 2022-05-28
What type Slack= appimage flatpak snap?
```
apt policy slack
slack:
  Installed: (none)
  Candidate: 1:0.15.2-9.1
  Version table:
     1:0.15.2-9.1 500
        500 http://ca.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        500 http://ca.archive.ubuntu.com/ubuntu jammy/universe i386 Packages

```
I'm kind of on a flatpak kick. :)
```
flatpak list
Name                Application ID                Version  Branch Installation
Slack               com.slack.Slack               4.26.1   stable system

```
On my current system I'm Snap-less ;)
```
snap list
Command 'snap' not found, but can be installed with:
sudo apt install snapd

```

---

