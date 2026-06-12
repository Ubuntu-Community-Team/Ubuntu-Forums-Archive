---
title: "Burn several mp4 as tracks on a dvd so any dvd player can play it"
date: 2015-07-28
forum: Multimedia Software
---

### Post by jake69 on 2015-07-28
I know this question has been asked many times over but I'm still having a hard time understanding what to do. If anyone could help me please please. ):P

I have 8 mp4 video files (each about a half hour long) that I would like to burn onto a dvd as tracks. I need it to play in **any **dvd player - even if the thing is 10 years old or an off brand or something. I'd like to watch the thing with friends in the future and have no way of knowing what kind of player they will have or what it's age might be.

What I hope to do is turn the individual files into tracks on the dvd, name the tracks, and have the dvd play so it plays all the way through unless you click a button / do something to make the track change. I have some blank DVD-R [DVD (minus) R], I'm running Ubuntu 14.04, and am most familiar with k3b, but I'm willing to install and learn any new software as long as I know exactly what I need to do to reach my goal.

Thank you for your kindness for any help.

----------------------------------------------------------

Edit:

I was googling around, trying to find some information, and I came across this : [http://www.bombono.org/cgi-bin/wiki/](http://www.bombono.org/cgi-bin/wiki/)

Could this be something I need? Anyone have experience with it.

---

### Post by shantiq on 2015-07-29
Jake you can use software called [devede]("https://en.wikipedia.org/wiki/DeVeDe") for this  it is in the repo

or [devedeNG]("http://www.rastersoft.com/programas/devede.html")   simple to use  ...   pick first option Create a DVD for all players

1.  download the [Deb]("http://www.rastersoft.com/descargas/python3-devedeng-jessie_4.0-debian2_all.deb")  from the site page
2.  install from terminal ```
sudo dpkg -i python3-devedeng-jessie_4.0-debian2_all.deb
```
3. find in your apps

---

### Post by jake69 on 2015-08-04
Right on. I've heard of devede before but wasn't sure if it's easy to use or did what I needed.

Can anyone tell me if I have to combine the mp4's into one file before doing this? Or can I run several mp4 through the process and end up with a dvd for any player?

---

### Post by shantiq on 2015-08-04
as many as you want Jake no need to splice first will do it for you use [devedeNG]("http://www.rastersoft.com/programas/devede.html") as it is designed SPECIFICALLY for ubuntu

---

### Post by jake69 on 2015-08-05
> **shantiq said:**
> as many as you want Jake no need to splice first will do it for you use [devedeNG]("http://www.rastersoft.com/programas/devede.html") as it is designed SPECIFICALLY for ubuntu

Thanks for letting me know what the difference was. Until I read that I really hadn't put any importance on NG. Now, personally speaking, I think it is important. Personally, I would rather use something meant for the operating system I'm running than not.

Peace
Jake

---

### Post by fredcarru on 2015-08-08
when I try 
sudo dpkg -i python3-devedeng-jessie_4.0-debian2_all.deb
I get 

dpkg: error processing archive python3-devedeng-jessie_4.0-debian2_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 python3-devedeng-jessie_4.0-debian2_all.deb
fred@fred-desktop:~$ sudo dpkg -i python3-devedeng-jessie_4.0-debian2_all.deb
dpkg: error processing archive python3-devedeng-jessie_4.0-debian2_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 python3-devedeng-jessie_4.0-debian2_all.deb

and I can't find devedeng in the software centre

---

### Post by shantiq on 2015-08-08
you have to be in the right directory Fred; the message says it was not found so not there in you Home directory

where is your deb situated? find it and place it on your Desktop manually

then  open terminal;  enter ```
cd ~/Desktop
```

then ; and I take it you have no other deb on your Desktop;    run  ```
sudo dpkg -i *.deb
```


That should do it :]

---

