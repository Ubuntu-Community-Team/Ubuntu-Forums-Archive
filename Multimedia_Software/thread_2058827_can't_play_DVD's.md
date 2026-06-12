---
title: "can't play DVD's"
date: 2012-09-16
forum: Multimedia Software
---

### Post by irv on 2012-09-16
Since Last December I haven't tried playing a DVD since installing 12.04 until today and DVD's will not play. I tried two different DVD and all I get is this error message. I do have all the extras installed so I am not sure what libraries they are talking about.
[ATTACH]224242[/ATTACH]

---

### Post by snowpine on 2012-09-16
Good instructions here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by irv on 2012-09-16
> **snowpine said:**
> Good instructions here: [https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Ran 
```
sudo apt-get install libdvdread4
```

But I already had libdvdread4 installed.
Then I ran
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
and this script fix the problem. Now the DVD's play.
Will mark solved.
Thanks for the help.

---

### Post by Segofam on 2012-10-13
> **irv said:**
> Ran 
```
sudo apt-get install libdvdread4
```

But I already had libdvdread4 installed.
Then I ran
```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
and this script fix the problem. Now the DVD's play.
Will mark solved.
Thanks for the help.

This worked for me also. I had been so frustrated as no player would work. Now at least VLC works again. Hopefully SMPlayer will work too now.

Thank you :)

---

