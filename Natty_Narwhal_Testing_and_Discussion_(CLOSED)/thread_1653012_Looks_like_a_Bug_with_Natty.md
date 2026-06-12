---
title: "Looks like a Bug with Natty"
date: 2010-12-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by smuthavarapu on 2010-12-26
Click on Desktop. From menu in the Top panel, Places --> Search For Files ?

Where is the Text Box to enter my search criteria ?

Edited
------------------
In Unity (11.04 Ubuntu Desktop Edition)

---

### Post by dino99 on 2010-12-26
no problem here on i386 (gnome, no unity)

---

### Post by smuthavarapu on 2010-12-26
I should have mentioned before this is in Unity

Search for the Text in Files is also missing.

---

### Post by mc4man on 2010-12-26
Until something is added for the Du or Cu login (Desktop > unity. Classic > unity) just use from terminal or create a launcher (can be added to launch panel if desired
```
gnome-search-tool
```

---

### Post by smuthavarapu on 2010-12-26
Thank you for the information.

But wondering about, why its not coming from Unity Desktop.

Will wait for next release then.

---

### Post by mc4man on 2010-12-26
> But wondering about, why its not coming from Unity Desktop.
It's December

---

### Post by wojox on 2010-12-26
> **smuthavarapu said:**
> Thank you for the information.

But wondering about, why its not coming from Unity Desktop.

Will wait for next release then.

That annoyed me as well. I went into Keyboard Shortcuts and created Ctrl+S for "Search" and all is normal again.

Also on Fedora 14 with Gnome 2.32.0 Ctrl+F opens the same "weird window".

---

### Post by davideotape on 2010-12-27
Has anyone reported a bug yet?

---

### Post by smuthavarapu on 2010-12-28
Logged the bug for the same

[https://bugs.launchpad.net/bugs/694954](https://bugs.launchpad.net/bugs/694954)

---

### Post by jennybrew on 2010-12-28
> **smuthavarapu said:**
> Click on Desktop. From menu in the Top panel, Places --> Search For Files ?


Just for avoidance of doubt ..can you let me know if I should be able to see top panel menu, including "Places" ..because at the moment I can't.

---

### Post by cariboo on 2010-12-28
You should see the places menu when you don't have any windows open by moving the mouse pointer to the left side of the top panel..

---

### Post by jennybrew on 2010-12-28
Thankyou Cariboo :)

---

### Post by JRV on 2010-12-29
> **mc4man said:**
> Until something is added for the Du or Cu login (Desktop > unity. Classic > unity) just use from terminal or create a launcher (can be added to launch panel if desired


How do you add a launcher to the launch panel?

---

### Post by cariboo on 2010-12-29
If you mean for a program, just start the program you want, then right-click the icon and select keep in Launcher. 

If you mean a launcher you created on the desktop, you can't.

---

### Post by dext on 2010-12-30
> **JRV said:**
> How do you add a launcher to the launch panel?

are you saying " how do you Add a shortcut to the panel " ?

---

### Post by ockron on 2010-12-30
Hi.

Can anyone please explain to me how I got natty on my PC as it's causing me endless problems.
Is there anyway I can go back, but please not back to windows again.

Thanx

---

### Post by dext on 2010-12-30
> **ockron said:**
> Hi.
[B]
Can anyone please explain to me how I got natty on my PC as it's causing me endless problems.[/B]
Is there anyway I can go back, but please not back to windows again.

Thanx

im sure none of us here have a crystal ball here. does anyone else have access to your PC? were you hacked?  if you wanna go back to Maverck reinstall it

---

### Post by cariboo on 2010-12-30
> **ockron said:**
> Hi.

Can anyone please explain to me how I got natty on my PC as it's causing me endless problems.
Is there anyway I can go back, but please not back to windows again.

Thanx

If About Ubuntu says you're running Natty, but:

```
cat /etc/lsb-release
```

says you are running Maverick, you are probably being affected by bug #[lpbug]694558[/lpbug]

---

### Post by JRV on 2010-12-30
> **dext said:**
> are you saying " how do you Add a shortcut to the panel " ?

Yes

---

