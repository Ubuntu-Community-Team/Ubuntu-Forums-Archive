---
title: "devede wont recognise mplayer"
date: 2009-12-03
forum: Multimedia Software
---

### Post by wokko on 2009-12-03
hey i solved it so dont worry about this post


Hi Guys

has anyone got the solution on how to get DeVeDe to recognise mplayer in karmic
have searched head to tail on this forum with no success , tried some of the ideas here but still dont work
even mplayer doesnt  work 
could someone help please
thanks David

---

### Post by Raffles10 on 2009-12-03
How did you install devede ? When you install using apt-get it will pull in mplayer as a dependency. I can use devede and mplayer ok in karmic having installed from the repo'. Try reinstalling:

```
sudo apt-get install devede
```

If the problem persists start devede from the terminal and check the errors when you close it.

---

### Post by wokko on 2009-12-03
cheers for the reply i tried to reinstall devede and now i have two in my menu so i tried starting from terminal and this is what i got


wokko@ wokko:~$ devede
DeVeDe 3.15.2
Locale: en_AU.UTF-8
Using package-installed files
/home/wokko/
Entro en fonts
Salgo de fonts
/home/wokko/
Temp Directory is:  /var/tmp
home load:  /home/wokko/.devede
linea:  video_format:pal

linea:  temp_folder:/var/tmp/

linea:  multicore:1

linea:  
/usr/bin/devede:295: GtkWarning: Could not load image 'devede.svg': Failed to open file '/usr/share/devede/devede.svg': No such file or directory
  arbol.add_from_file(os.path.join(glade,"wprograms.ui"))
/home/wokko/

---

### Post by wokko on 2009-12-04
hey guys just done a fresh install of ubuntustudio and put in all the extra repos and installed devede and seem to fix the problem

---

