---
title: "evince problem, anyone else have this?"
date: 2010-05-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by mdurham on 2010-05-26
Hi, as the Title suggests, evince Ver 2.30.1-2ubuntu1 doesn't work, is it just me?
Running from a terminal produces the following.
> mike$ evince

(evince:2307): EggSMClient-WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported


(evince:2307): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/mike/.recently-used.xbel', but the parser failed: Failed to open file '/home/mike/.recently-used.xbel': Permission denied.

** (evince:2307): WARNING **: Error creating last_settings file: Error opening file '/home/mike/.gnome2/evince/last_settings': Permission denied

Segmentation fault
mike$ 


Cheers

---

### Post by Framli on 2010-05-26
Deleting the evince folder in /home/$USER/.gnome2/ solved it for me.

David

---

### Post by mdurham on 2010-05-26
> **Framli said:**
> Deleting the evince folder in /home/$USER/.gnome2/ solved it for me.

David

Thanks for the suggestion David. Unfortunately it didn't work, it's still exactly the same.
Cheers, Mike

---

### Post by crjackson on 2010-05-26
Hummm.... seems to be working fine for me.

---

### Post by LKjell on 2010-05-27
> **mdurham said:**
> Hi, as the Title suggests, evince Ver 2.30.1-2ubuntu1 doesn't work, is it just me?
Running from a terminal produces the following.


Cheers

Try to remove the files that have the permission error. You might also want to try the guess user or create another user to see if you have the same problems

---

### Post by TheForkOfJustice on 2010-05-28
May not be related but I'm having problems with evince in Debian testing right now.  Won't load anything.  Just fails.

[http://packages.debian.org/squeeze/evince](http://packages.debian.org/squeeze/evince)

Same version: 2.30

---

### Post by TheForkOfJustice on 2010-05-28
Ran it in terminal to see what would happen:

```

mackinal@LFCWORK-Debian:~/Downloads$ evince ./BaylorDNAform.pdf

** (evince:2789): WARNING **: Error creating last_settings file: Error opening file '/home/mackinal/.gnome2/evince/last_settings': No such file or directory

Segmentation fault
```


Fixed problem in Debian by doing this:

mkdir ~/.gnome2/evince
touch ~/.gnome2/evince/last_settings

Works now.  That folder and file should be created when absent but isn't.

---

### Post by mdurham on 2010-05-28
> **TheForkOfJustice said:**
> Ran it in terminal to see what would happen:

```

mackinal@LFCWORK-Debian:~/Downloads$ evince ./BaylorDNAform.pdf

** (evince:2789): WARNING **: Error creating last_settings file: Error opening file '/home/mackinal/.gnome2/evince/last_settings': No such file or directory

Segmentation fault
```


Fixed problem in Debian by doing this:

mkdir ~/.gnome2/evince
touch ~/.gnome2/evince/last_settings

Works now.  That folder and file should be created when absent but isn't.

Thanks TheForkOfJustice, I did your suggestion above and it now works but I still get errors. Never mind, at least it works.
> (evince:2307): EggSMClient-WARNING **: Failed to connect to the session manager: None of the authentication protocols specified are supported


(evince:2307): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/mike/.recently-used.xbel', but the parser failed: Failed to open file '/home/mike/.recently-used.xbel': Permission denied.


---

### Post by zika on 2010-05-28
Did You, by any chance, use **sudo** with some GUI applications (instead of **gksu**)... That looks (to me) like some problem with permissions...

---

### Post by mdurham on 2010-05-28
> **zika said:**
> Did You, by any chance, use **sudo** with some GUI applications (instead of **gksu**)... That looks (to me) like some problem with permissions...
I don't think that I used **sudo** instead of **gksu** any time, but what has that got to do with evince?.

---

### Post by seeker5528 on 2010-05-28
> **mdurham said:**
> I don't think that I used **sudo** instead of **gksu** any time, but what has that got to do with evince?.

If you use sudo, without any options, programs in that sudo session that write to the home directory will write to your home directory, but with root ownership, this happens whether it is a program with a GUI or not. Then when you run the program normally, you may have issues when you can't create/save files because of file or directory permissions resulting from the stuff with root ownership causing file creation or overwriting of an existing file to fail.

If you use the -H option with sudo 'sudo -H some-command' it will change the home directory, typically to root, gksudo and kdesudo do something to prevent problems like this automatically plus some additional X credentials voodoo.

Later, Seeker

---

### Post by mdurham on 2010-05-28
> **seeker5528 said:**
> If you use sudo, without any options, programs in that sudo session that write to the home directory will write to your home directory, but with root ownership, this happens whether it is a program with a GUI or not. Then when you run the program normally, you may have issues when you can't create/save files because of file or directory permissions resulting from the stuff with root ownership causing file creation or overwriting of an existing file to fail.

If you use the -H option with sudo 'sudo -H some-command' it will change the home directory, typically to root, gksudo and kdesudo do something to prevent problems like this automatically plus some additional X credentials voodoo.
Later, Seeker
I see, thanks for that seeker5528.

---

