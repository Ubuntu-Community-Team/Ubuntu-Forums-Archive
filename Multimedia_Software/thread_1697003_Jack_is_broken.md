---
title: "Jack is broken"
date: 2011-02-28
forum: Multimedia Software
---

### Post by cliff01 on 2011-02-28
I cannot get the jack control window to open. I uninstalled and reinstalled twice and no change. What information can I post to help you help me? I have sound but would like to get Rosegarden running with Qsynth. Thank you for any help here.

---

### Post by cchhrriiss121212 on 2011-02-28
Open a terminal and type this:
qjackctl

Should show you an error message of some sort.

---

### Post by cliff01 on 2011-02-28
Thanks for the response, but nothing happened. No error message, no anything. Another reinstall perhaps??

---

### Post by cchhrriiss121212 on 2011-02-28
Open up system monitor and check the processes for any instance of jackd or qjackctl.

---

### Post by cliff01 on 2011-03-01
After entering "qjackctl" in the terminal, qjackctl was listed as one of the processes. Status is sleeping... The control center did not appear on the desktop though.

---

### Post by cchhrriiss121212 on 2011-03-02
With no error messages, there is not much I can suggest. Have you any other programs that do this? Could try deleting all the config files you find, look in /home/user/.config or do a search for them with catfish.

You should be able to use qsynth and rosegarden without jack though, just set them to use ALSA, then use aconnectgui to hook them up.

---

