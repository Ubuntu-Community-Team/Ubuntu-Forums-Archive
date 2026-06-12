---
title: "Sopcast Player has stopped working suddenly!"
date: 2011-12-10
forum: Multimedia Software
---

### Post by Vetinarisdog on 2011-12-10
Running Ubuntu 11.10 and managed to get Sopcast Player and installed and working with no problems (have never had it working under previous distros).  However, now whenever I click on the launch icon nothing happens whatsoever.  Anyone any ideas?

---

### Post by howefield on 2011-12-10
Try starting it from a terminal, you'll most likely get a clue to the problem in the output.

---

### Post by Vetinarisdog on 2011-12-10
> **howefield said:**
> Try starting it from a terminal, you'll most likely get a clue to the problem in the output.

Thanks.  Weird as I have altered nothing I get this...


> sopdavid@david-AOA150:~$ sopcast-player

(sopcast-player.py:10440): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(sopcast-player.py:10440): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(sopcast-player.py:10440): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(sopcast-player.py:10440): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Traceback (most recent call last):
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 36, in <module>
    from VLCWidget import VLCWidget
  File "/usr/share/sopcast-player/lib/VLCWidget.py", line 32, in <module>
    import vlc_1_0_x
ImportError: No module named vlc_1_0_x

Would an update have caused this?  Any idea how to rectify?

---

### Post by howefield on 2011-12-10
> **Vetinarisdog said:**
> Would an update have caused this?  Any idea how to rectify?

Could be.

Not sure what versions you are using but on 11.10 I installed sopcast version 0.7.4 using the ppa from here..

[https://launchpad.net/~jason-scheunemann/+archive/ppa](https://launchpad.net/~jason-scheunemann/+archive/ppa)

and VLC version 1.1.12 from the Ubuntu repository, seems to work fine.

---

### Post by Vetinarisdog on 2011-12-10
> **howefield said:**
> Could be.

Not sure what versions you are using but on 11.10 I installed sopcast version 0.7.4 using the ppa from here..

[https://launchpad.net/~jason-scheunemann/+archive/ppa](https://launchpad.net/~jason-scheunemann/+archive/ppa)

and VLC version 1.1.12 from the Ubuntu repository, seems to work fine.

Yeah, using the same but still getting the error.  Tried removing and re-installing but no joy.:(

---

### Post by Bo Rosén on 2011-12-12
I get the same error with the ferramroberto repo. New install.

Anyone?

---

### Post by Vetinarisdog on 2011-12-14
Okay so did a complete re-install and same problem occurs.  I think it might be a problem with VLC given the errors shown above.  Any ideas?

---

### Post by dimmu_stranger on 2011-12-14
I had the same problem, this is my solution:
1) i saw an error (ImportError: No module named vlc_1_0_x)
2) goes to /usr/share/sopcast-player/lib/
3) do "ls -la | grep vlc"
4) output: vlc_1_1_x.py vlc_1_1_x.pyc
5) there is no vlc_1_0_x!
6) making a hardlink "sudo ln -s vlc_1_1_x.py vlc_1_0_x.py"
7) trying to launch sopcast - it's fine now.

PS: i'm running ubuntu 11.10 amd64, vlc 1.1.5-1, sopcast-player 0.7.4-4.1~lffl~oneiric~ppa

---

### Post by Vetinarisdog on 2011-12-15
> **dimmu_stranger said:**
> I had the same problem, this is my solution:
1) i saw an error (ImportError: No module named vlc_1_0_x)
2) goes to /usr/share/sopcast-player/lib/
3) do "ls -la | grep vlc"
4) output: vlc_1_1_x.py vlc_1_1_x.pyc
5) there is no vlc_1_0_x!
6) making a hardlink "sudo ln -s vlc_1_1_x.py vlc_1_0_x.py"
7) trying to launch sopcast - it's fine now.

PS: i'm running ubuntu 11.10 amd64, vlc 1.1.5-1, sopcast-player 0.7.4-4.1~lffl~oneiric~ppa

No joy.

Still get this...


Traceback (most recent call last):
  File "/usr/share/sopcast-player/lib/sopcast-player.py", line 36, in <module>
    from VLCWidget import VLCWidget
  File "/usr/share/sopcast-player/lib/VLCWidget.py", line 32, in <module>
    import vlc_1_0_x
ImportError: No module named vlc_1_0_x


Anyone?:(

---

### Post by d.atanasov on 2011-12-16
I have the same error while starting from terminal. Maybe this is caused by a dependency on the older version of vlc player. Does anyone know how to configure it with the newest vlc 1.1.x ? Does anyone found a solution meanwhile?

greetings

---

### Post by d.atanasov on 2011-12-16
Ok I found a bit work around:

```
locate *VLCWidget*
```

then you should open for editing: 

```
sudo nano /usr/share/sopcast-player/lib/VLCWidget.py
```

then find the line:

```
import vlc_1_0_x
```

and comment it like this:

```
#import vlc_1_0_x
```

Save the file and start the sopcast-player. This works for me. I hope for you too :)

greetings

---

### Post by davdo2004 on 2011-12-16
The 2 lines that refer to 'vlc_1_0_x' need to be changed to 'vlc_1_1_x'
```

gksu gedit /usr/share/sopcast-player/lib/VLCWidget.py

```

---

### Post by Wingsgb on 2011-12-17
> **davdo2004 said:**
> The 2 lines that refer to 'vlc_1_0_x' need to be changed to 'vlc_1_1_x'
```

gksu gedit /usr/share/sopcast-player/lib/VLCWidget.py

```


thanks for the help my sopcast is now working :) just intime for the fight

thanks again

---

### Post by ueghio on 2012-04-08
> **d.atanasov said:**
> Ok I found a bit work around:

```
locate *VLCWidget*
```

then you should open for editing: 

```
sudo nano /usr/share/sopcast-player/lib/VLCWidget.py
```

then find the line:

```
import vlc_1_0_x
```

and comment it like this:

```
#import vlc_1_0_x
```

Save the file and start the sopcast-player. This works for me. I hope for you too :)

greetings

Works for me too!thanks

---

