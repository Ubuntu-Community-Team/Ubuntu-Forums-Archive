---
title: "Flash Problem"
date: 2009-07-25
forum: Multimedia Software
---

### Post by Joseph.M on 2009-07-25
I am a fairly new Ubuntu user, and so far ive been loving it except for one small problem. I wanted to upgrade my flash player because when I used multiple flash applications at once Ex. Pandora and Texas Hold'em from facebook It would randomly freeze up and sometimes Hulu would do the same. I found [This Thread]("http://ubuntuforums.org/showthread.php?t=772490") and used the one that was applicable to me which i though was 64bit Flash Alpha* but now i caint do anything pertaining to flash if i get on Pandora, Hulu, or try to play Texas Holed'em on facebook the browsers automatically close without warning. Is there any way to fix this or go back to the older version?

---

### Post by wojox on 2009-07-25
Here you go for the latest version:

[http://psychocats.net/ubuntu/flash](http://psychocats.net/ubuntu/flash)

---

### Post by conradin on 2009-07-25
> **Joseph.M said:**
> I am a fairly new Ubuntu user, and so far ive been loving it except for one small problem. I wanted to upgrade my flash player because when I used multiple flash applications at once Ex. Pandora and Texas Hold'em from facebook It would randomly freeze up and sometimes Hulu would do the same. I found [This Thread]("http://ubuntuforums.org/showthread.php?t=772490") and used the one that was applicable to me which i though was 64bit Flash Alpha* but now i caint do anything pertaining to flash if i get on Pandora, Hulu, or try to play Texas Holed'em on facebook the browsers automatically close without warning. Is there any way to fix this or go back to the older version?


So, you question is how to remove a plugin? you might try something like:
```

sudo apt-get remove flashplugin-nonfree

```
```

sudo apt-get remove --purge flashplugin-nonfree

```

If that doesnt do it, I would do 
```

dpkg -l 

```
to try and find the name of the plugin, and uninstall it.

---

### Post by Joseph.M on 2009-07-25
Thanks for the help, got it to where i can veiw/play flash.

---

### Post by lovinglinux on 2009-07-25
For future reference...

[**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by allzzzzz on 2009-07-25
when i try to update my flash i get to the point where u hit install after the loading window goes away and the button wont light up and it states dependencies  are unsatisfiable, then libcairo...something  mssg me for more details...plz

---

