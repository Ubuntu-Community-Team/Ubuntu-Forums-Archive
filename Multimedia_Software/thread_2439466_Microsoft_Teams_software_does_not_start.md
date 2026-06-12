---
title: "Microsoft Teams software does not start"
date: 2020-03-28
forum: Multimedia Software
---

### Post by ninos on 2020-03-28
Microsoft Teams software does not start

---

### Post by webaake on 2020-03-28
Following....

---

### Post by slickymaster on 2020-03-28
If you want to get the proper help to the issues you're facing, please include as many details as you can. For example, operating system, software version numbers or computer hardware specifications.

---

### Post by ninos on 2020-03-28
ubuntu 18.04
i installed the deb file of the proprietary software
the icon appears
but when i click it 
it seams to work ("Microsoft teams preview" is shown ) but after a few seconds it just stops
teams never actually opens

also on the terminal
emmanuel@emmanuel-ThinkPad-X240:~$ teams
emmanuel@emmanuel-ThinkPad-X240:~$ 

without  any error message...

I've sent the problem report to developers twice

---

### Post by ninos on 2020-03-30
well, i removed the proprietary package from microsoft
i installed the one from github
[https://github.com/ivelkov/teams-for-linux/releases/download/v0.0.7/teams-for-linux_0.0.7_amd64.deb](https://github.com/ivelkov/teams-for-linux/releases/download/v0.0.7/teams-for-linux_0.0.7_amd64.deb)
and problem solved

---

### Post by amendt on 2020-05-20
I tried both proprietary packages and it still crashes on application startup

---

### Post by SeijiSensei on 2020-05-21
I'd avoid the problem entirely by installing VirtualBox, then creating a virtual machine running Windows.

---

