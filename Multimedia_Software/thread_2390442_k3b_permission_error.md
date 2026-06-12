---
title: "k3b permission error"
date: 2018-04-28
forum: Multimedia Software
---

### Post by missmoondog on 2018-04-28
hello,
just upgraded a couple computers to 18.04, both 64bit, and get a permission error for cdrecord when trying to burn any kind of disc. done some searching and haven't found solution yet. time to ask!

forget exact wording now but pretty close to what i said. if i run k3b through terminal using sudo k3b i get no errors. it says to change permission under tools/configure k3b but i'm not seeing anything that does it. never had any issues with k3b before.

any suggestions?

thank you

---

### Post by Yellow Pasque on 2018-05-01
1. Make sure your user is listed as part of cdrom group in /etc/group
2. Check "use burning group" and name the group cdrom

---

### Post by allenbeme on 2018-05-01
I had this same error (could not create an audio CD) with brasero and K3b. I can create data CDs no problem, but not audio CDs. Following the advice below, I installed Xfburn and created an audio CD successfully.

---

### Post by missmoondog on 2018-05-02
@Temujin:
ok, how do i do that? i'm kind of incompetent at this stuff. :(

@allenbeme:
xfburn was already installed but i like k3b much better, but i'm using it in the mean time.

---

### Post by Yellow Pasque on 2018-05-02
```
cat /etc/group | grep cdrom
```
If it returns a line with your username (e.g. cdrom:x:24:username), then you're a part of the cdrom group.

One of K3b's settings dialogs is for permissions. That is where you will find the option to "use burning group" and you can check it. Make sure you change the group to cdrom (I think the default group name is 'burning').

---

### Post by missmoondog on 2018-05-03
i saw where it has the permissions in k3b's settings, but no way to change anything there, that i see.

thanks for the info. will check into it next time i'm on my own computer.

---

### Post by missmoondog on 2018-05-05
@Temujin
when i run that command i do get cdrom: x:24:missmoondog

under the permissions i see no option to use burning group though. now with leaving k3b open for a few minutes while looking through it, it keep crashing and closing.

---

