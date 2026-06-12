---
title: "No sound when run with su -"
date: 2016-08-23
forum: Multimedia Software
---

### Post by rick3332 on 2016-08-23
I am trying to create a non privileged user who can own a  web browser profile and files and whatnot. I want to see and hear any apps that are run as this user on the main users screen. It seems to work great so far, but I get no sound. Here is what I have done:

xhost +SI:localuser:rick

#Then for firefox:
su -c "firefox &" - rick

#or to change users in the current terminal, then I can run firefox at the new prompt:
su  - rick

How do I get sound too? I am running Xenial.

---

