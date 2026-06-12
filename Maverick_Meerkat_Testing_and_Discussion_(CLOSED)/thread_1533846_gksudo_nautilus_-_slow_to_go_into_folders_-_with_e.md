---
title: "gksudo nautilus - slow to go into folders - with error"
date: 2010-07-18
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by 23dornot23d on 2010-07-18
This is after a clean install from the daily build CD and the latest kernel today .....

I get this warning when using Nautilus when I navigate through folders by clicking on them,

and it is extremely slow .....  

** (nautilus:2036): WARNING **: Error calling get_folders: Launch helper exited with unknown return code 1

( But on a good note the latest build flies on other things like the boot up time.........)

Full output ..... although .... it continues to give the same error .... while I am using it ....... 

> 
keith@keith-laptop:/var/log/bootchart$ gksudo nautilus
Initializing nautilus-gdu extension

** (nautilus:2036): WARNING **: Error calling get_folders: Launch helper exited with unknown return code 1

** (nautilus:2036): WARNING **: Error calling get_folders: Launch helper exited with unknown return code 1
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:2036): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.config/user-dirs.dirs


** (nautilus:2036): WARNING **: Error calling get_folders: Launch helper exited with unknown return code 1

I can do the same command using THUNAR ,,,,, no errors and it flies through the selections

keith@keith-laptop:/var/log/bootchart$ gksudo thunar
keith@keith-laptop:/var/log/bootchart$


Interesting I just saw this in the other thread for Ubuntu one  ,,,,,,,,,
I dont use it so purged it ......... the error went away too

> 
                                  **Re: Ubuntu One in nautilus**             
                                                                sudo apt-get purge ubuntuone-client-gnome

Thanks for this!  I'm using a netbook and there's no real estate to  spare.  The banner in Nautilus for Ubuntu One with no choice given to  close it was a bit of a problem.

I just purged UBUNTU one ...... and now no errors .......

But its still SLOW ....

---

### Post by mc4man on 2010-07-18
> But its still SLOW ....
Not sure if the slowness is caused by  ubuntuone (ubuntuone-syncd), on my 'real' install am keeping for the moment as a file sharer (useless for storage in a backup sense.

But on a live cd removing all ubuntuone* packages and logging out/in restored browing as root to normal

(before logging out ubuntuone-syncd continued to run even after all the ubuntuone packages were removed

Though sometimes results from live cd can be suspect..

---

### Post by 23dornot23d on 2010-07-18
When I re-booted the speed returned to Nautilus when going through the directories.

Can now navigate faster ...... so must have been related to Ubuntu One ......

Seems a lot better now.

---

### Post by mc4man on 2010-07-18
Well then it would seem ubuntuone-syncd may be the culprit here.

Is back to normal w/ updates thru 0/21

---

### Post by MarkieB on 2010-08-02
as for the actual bug being [solved] I'm not convinced, I'm seeing really slow nautilus even now, [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/610725](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/610725)

I suppose I'll be uninstalling ubutu one; although the music store aspect seemed pleasant, it too was awfully slow at changing pages / loading etc

---

### Post by suito on 2010-08-02
Had a lot of troubles with Nautilus, namely it being slow as hell.

Just removed ubuntuone and ubuntuone-gnome, ran "nautilus -q" and now it's all fine.

---

### Post by blackest_knight on 2010-08-17
I had problems with nautilus just not responding for a minute or more the difference after removing ubuntu-one client was remarkable even launching programs feels faster. this is native having upgraded from lucid to alpha3 unfortunately I now have to use desktop mode since netbook mode is terrible in maverick. Having a dock continually visible is a really bad idea.

---

### Post by cariboo on 2010-08-17
@blackest_knight, why post in a thread that's solved. If you don't like Unity, this sub-forum is not the place for opinions. Please create a thread in the [Cafe]("http://ubuntuforums.org/forumdisplay.php?f=11") if you want to state your opinion. This thread is **Closed.**

---

