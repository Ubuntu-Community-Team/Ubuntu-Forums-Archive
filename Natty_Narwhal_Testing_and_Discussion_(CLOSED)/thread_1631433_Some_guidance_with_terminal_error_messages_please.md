---
title: "Some guidance with terminal error messages please"
date: 2010-11-26
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Quackers on 2010-11-26
I have 2 recent Natty re-installs.
On both of them I have done several grub changes, including grub splash images and deleting Memtest and recovery menu entries. I have also done many similar changes in other installations, 10.04 and 10.10
I usually use gksu gedit /etc/default/grub to make the changes and have no problems.

In the last couple of days I have been trying to delete recovery items from the grub menu in both Natty installs but am getting errors in the terminal window. The first couple of errors appear as soon as I execute the gksu command and the other errors appear on trying to save the changes I've made. I even tried sudo gedit /etc/default/grub but got the errors in the second display.
```
natty64@natty64-VGN-AR51SU:~$ gksu gedit /etc/default/grub

(gedit:1731): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.FV35LV': No such file or directory

(gedit:1731): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1731): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.VZWLMV': No such file or directory

(gedit:1731): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
```

```
natty64@natty64-VGN-AR51SU:~$ sudo gedit /etc/default/grub

(gedit:2397): Gtk-WARNING **: Unable to rename '/root/.recently-used.xbel': No such file or directory

(gedit:2397): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.O3WHMV': No such file or directory

(gedit:2397): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2397): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.9FQNMV': No such file or directory

(gedit:2397): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2397): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.6D8DMV': No such file or directory

(gedit:2397): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
natty64@natty64-VGN-AR51SU:~$
```

And gksudo gives simlar errors.

Am I missing something? 
Am I doing something wrong?
Is it a bug in Natty?

Thanks for your time :-)

---

### Post by Reiger on 2010-11-26
It means that the directory /root/.local/share/ does not exist. 

Workaround (1): ignore the issue, (2) create that directory manually.

Solution don't use gedit or gksudo to edit files with elevated permissions. Use sudo in combination with commandline tools instead such as e.g. nano. It is not a bug it is simply using the wrong tools (GTK apps) for the job (sensitive system administration tasks): you see the GTK app attempting to spew random garbage as root.

---

### Post by Quackers on 2010-11-26
I appreciate the advice.
However I tried to create the file using sudo touch and permission was denied. If you could shed some light in this area it would be appreciated.

Your answer also brings up some questions.
I have used this same guide by a member of staff here dozens of times in Lucid, Meerkat AND Natty without any problems at all. It is only the last couple of days where this problem has occurred and only in Natty.
So it begs the question is Natty using a different file to store the changes temporarily or is Natty not creating the necessary file for some reason?

I have also attempted to use sudo nano without success.

Any guidance would be appreciated.

---

### Post by MacUntu on 2010-11-26
How is editing a text file with a text editor using the wrong tool? IMO this is just a gedit bug (or GTK+ or whichever package is responsible for trying to write that file).

---

### Post by Quackers on 2010-11-26
> **MacUntu said:**
> How is editing a text file with a text editor using the wrong tool? IMO this is just a gedit bug.

That would seem to be the obvious answer to me.
I was after clarification, not a telling off :-)

---

### Post by Reiger on 2010-11-26
This is not a GTK/gedit bug but a GTK/gedit feature getting in your way. Considering this GTK/gedit behaviour to track last used files a bug is much like complaining that a hammer doesn't work very well when attempting to fit screws.

Again if you want to, you can ignore the problem or create that directory to make the warnings go away; alternatively you can solve it by not using GTK/gedit for tasks it is not intended to do (system administration).

---

### Post by ronacc on 2010-11-26
> **Reiger said:**
> This is not a GTK/gedit bug but a GTK/gedit feature getting in your way. Considering this GTK/gedit behaviour to track last used files a bug is much like complaining that a hammer doesn't work very well when attempting to fit screws.

Again if you want to, you can ignore the problem or create that directory to make the warnings go away; alternatively you can solve it by not using GTK/gedit for tasks it is not intended to do (system administration).

I beg to differ with you , either gedit is fubar right now or something else is . I have gedit 2.91.2-0ubuntu1~build2 installed (amd64) and am up to date . when I try to start gedit I get 

```
ron@ron-desktop2:~$ gedit

** (gedit:12482): WARNING **: Could not load Gedit repository: Typelib file for namespace 'Gedit', version '3.0' not found

(gedit:12482): libpeas-WARNING **: Type not found in introspection: 'GeditAppActivatable'

** (gedit:12482): CRITICAL **: g_callable_info_get_n_args: assertion `info != NULL' failed

** (gedit:12482): CRITICAL **: g_callable_info_get_n_args: assertion `info != NULL' failed

** (gedit:12482): CRITICAL **: g_callable_info_get_arg: assertion `info != NULL' failed

** (gedit:12482): CRITICAL **: g_arg_info_get_type: assertion `info != NULL' failed

** (gedit:12482): CRITICAL **: g_arg_info_get_direction: assertion `info != NULL' failed
Segmentation fault
ron@ron-desktop2:~$ 
``` 
note just straight gedit no sudo or gksu . trying to start from icon the same except ofcourse it don't tell why it isn't starting , furthermore running ```
 ubuntu-bug gedit 
``` returns that this is not a genuine ubuntu package ????

---

### Post by Quackers on 2010-11-26
As I have said I have tried to create the file and it failed.
Your comments do not answer the point that the same commands have been used dozens of times in 3 different Ubuntu flavoured installs without any problem. This includes Natty. The last time was 3 days ago! Why then and not now?  This is partly my point.

As I said previously I am following a guide by a member of staff which I have used many times without problems.

---

### Post by Reiger on 2010-11-26
> **ronacc said:**
> I beg to differ with you , either gedit is fubar right now or something else is . I have gedit 2.91.2-0ubuntu1~build2 installed (amd64) and am up to date . when I try to start gedit I get 

... a completely different problem? Look at the warnings in the OP and compare them with the broken mess your gedit is in. Not nearly the same thing is it? :p

Post #1 is about GTK/gedit tracking some meta information about what files were last edited (going by the name of the file). This requires a proper environment be set up in the user's home directory (under ~/.local, which in case of root maps to /root/.local/) which appears not to be the case for the user “root”.

---

### Post by ronacc on 2010-11-26
I was indicating that gedit is having problems right now , The OP's complaint is a bug , I have been using gedit with root privileges for years without ever having to specifically create a "/root/.local/share/recently-used.xbel" or ANY file in /root . That file should be created by gedit itself without any user interaction .

---

### Post by Reiger on 2010-11-26
> **MacUntu said:**
> How is editing a text file with a text editor using the wrong tool? IMO this is just a gedit bug (or GTK+ or whichever package is responsible for trying to write that file).

This is a GUI application built on top of libraries which make no security guarantees, no file locking guarantees or anything. So that means a large amount of code running with permissions it was never meant/designed to cope with (GTK/Xlib/gedit proper). On top of that the code assumes a functioning GNOME environment (or at least a functional ~/.local/share) which in the case of the user root is a big assumption to make (because root was never meant to run any desktop at all).

Hence that's why I think using gedit for editing files as root is equivalent to using the wrong tool for the job, regardless of whether the guide followed was written by a member of staff or the work of monkeys with typewriters. 

FWIW there is sudoedit, or alternatively you can cp files around, chown them and delete temporary copies afterwards manually.

---

### Post by Quackers on 2010-11-26
Again, thank you for your comments Reiger.
You seem unable or unwilling to comment on the fact that all my transgressions, or protocol breaches, worked 3 days ago on the same 2 systems, but not now. Surely something has changed in that time for the errors to appear now.

In all honesty it seems to me that quote "alternatively you can cp files around, chown them and delete temporary copies afterwards manually" unquote seems a long journey just to edit a text file.

---

### Post by ronacc on 2010-11-26
> **Reiger said:**
> (because root was never meant to run any desktop at all).

pray tell then why ANY gui root only apps are PROVIDED by the DT ? For instance synaptic or  just about anything in the admin menu .

---

### Post by MacUntu on 2010-11-27
> **Reiger said:**
> This is not a GTK/gedit bug but a GTK/gedit feature getting in your way.

No, this is a bug - it has nothing to do with permissions. Move away your user's /home/.local/share folder and start gedit.

As you say:

> **Reiger said:**
> On top of that the code assumes

-> famous last words.

---

### Post by Reiger on 2010-11-27
> **Quackers said:**
> Again, thank you for your comments Reiger. You seem unable or unwilling to comment on the fact that all my transgressions, or protocol breaches, worked 3 days ago on the same 2 systems, but not now. Surely something has changed in that time for the errors to appear now. Surely, but nothing relevant to the particular terminal messages. These messages do not point out a bug in and of themselves. They are merely side effects of using gedit in a situation it was not built to be in. 

I don't know how to put this more explicitly but there is a difference between the problem you report (gedit run as root is unable to create some irrelevant meta data file in /root/.local/share/) and being unable to save an edited text file as root. The difference is that in one case gedit simply runs into a problem that is not its “own fault” as it were, the latter would be gedit failing as an editor. The latter is a different issue altogether (and probably a bug).

> In all honesty it seems to me that quote "alternatively you can cp files around, chown them and delete temporary copies afterwards manually" unquote seems a long journey just to edit a text file.

Yes, hence sudoedit to do it for you. By far the superior choice. I'm not saying you cannot use gedit by definition, what I am saying is that gedit/GTK/Xlib was never supposed to deal with the responsibility of being root hence you are going to see things that look like bugs but really aren't. And there's no fix other than not running gedit/GTK/Xlib as root.

[quote=MacUntu]
No, this is a bug - it has nothing to do with permissions.[/quote]
Where did you get that this had anything to do with permissions? I said it had to do with a particular directory not existing. As it so happens the directory which does not exist is a directory which is not supposed to exist in the first place. (~/.local being what it is). 

> Move away your user's /home/.local/share folder and start gedit.


Precisely the point: gedit assumes a working desktop environment installation, with ~/.local tree and all. It warns when it doesn't find one. For /root no such tree ought to exist (it is created on first run of a desktop session, which root is never supposed to do).

So how again is it a bug when an application warns about something missing which ought to exist under normal conditions?

More precisely how is it a bug that /root does not contain .local/share directory when root is not supposed to run a desktop environment itself? 
How is it a bug that gedit assumes a working desktop environment, being written to fit a particular desktop environment? 
How is it a bug that gedit warns about not having a ~/.local/share (however cryptic) when there is no ~/.local/share ?

[quote=ronacc]
pray tell then why ANY gui root only apps are PROVIDED by the DT ? For instance synaptic or just about anything in the admin menu .
[/quote]

For the same reason why the kernel supports hardware that isn't manufactured anymore. It's legacy, but still useful. However you will have noticed that there is a shift away from the old & buggy & less secure ways to a backend + frontend approach (policykit anyone?). This fixes all sorts of issues (not just security related ones either: improper themes/settings for instance).

---

### Post by ronacc on 2010-11-27
> **Reiger said:**
> 

Precisely the point: gedit assumes a working desktop environment installation, with ~/.local tree and all. It warns when it doesn't find one. For /root no such tree ought to exist (it is created on first run of a desktop session, which root is never supposed to do).

So how again is it a bug when an application warns about something missing which ought to exist under normal conditions?

More precisely how is it a bug that /root does not contain .local/share directory when root is not supposed to run a desktop environment itself? 
How is it a bug that gedit assumes a working desktop environment, being written to fit a particular desktop environment? 
How is it a bug that gedit warns about not having a ~/.local/share (however cryptic) when there is no ~/.local/share ?



For the same reason why the kernel supports hardware that isn't manufactured anymore. It's legacy, but still useful. However you will have noticed that there is a shift away from the old & buggy & less secure ways to a backend + frontend approach (policykit anyone?). This fixes all sorts of issues (not just security related ones either: improper themes/settings for instance).

There are distros , Puppy for one , where you ALWAYS run as root . While running as root does incur security risks it is sometimes the easiest and most practical way to accomplish a task , gui's were invented for more than just eyecandy . and to use your own example , hammers are certainly a "legacy" piece of hardware , ( a rock used to hammer another rock was the first stone tool ) , they are still very useful even though the screwdriver works better FOR SCREWS .

---

### Post by Reiger on 2010-11-27
> **ronacc said:**
> There are distros , Puppy for one , where you ALWAYS run as root .
I know, I've a puppy 4 USB stick lying around somewhere; penetration testing distro's do that as well btw. Doesn't mean it is good practice even for system admin tools though. It simply means that for some distro's the complexity of setting up a proper user account environment is more than they're willing to do for the gains it brings them.

> While running as root does incur security risks it is sometimes the easiest and most practical way to accomplish a task , gui's were invented for more than just eyecandy .

Agreed.

>  and to use your own example , hammers are certainly a "legacy" piece of hardware , ( a rock used to hammer another rock was the first stone tool ) , they are still very useful even though the screwdriver works better FOR SCREWS .

So you see why using a screwdriver when dealing with screws is preferable to using a hammer. Likewise why using a tool built to deal with editing system config files in a more secure context (sudoedit) is preferable to using the text editor built to support every day gardening variety text based tasks as part of a desktop environment?

---

### Post by Quackers on 2010-11-27
It still worked 4 days ago but doesn't now. Something changed somewhere.

---

### Post by seeker5528 on 2010-11-27
> **Reiger said:**
> Surely, but nothing relevant to the particular terminal messages. These messages do not point out a bug in and of themselves. They are merely side effects of using gedit in a situation it was not built to be in.

The first time you run gedit these '.local/*/' directories would not exist and gedit should create them and whatever files it needs.

Failure to do so is a bug whether .local is in your actual home directory or whether you gksudo it and '/root/' is set as home for the sudo session.

Later, Seeker

---

### Post by ronacc on 2010-11-27
sudoedit does not give me a file selector to browse to the file I want to edit ( the exact name of which I may not know  ) nor does it have the context formating for editing executable scripts nor does it provide tabs so that different files can be easily compared . IMHO that makes it a waste of good disk space , you of course are entitled to you opinion .

---

### Post by MacUntu on 2010-11-27
> **Reiger said:**
> So how again is it a bug when an application warns about something missing which ought to exist under normal conditions?

A warning is okay, loss of functionality isn't. I totally understand your point, but really, what's wrong with spitting out a warning AND creating that directory/file? After all, I explicitly asked gedit to work (even if that clutters my ought to be "empty" root dir).

> **Reiger said:**
> How is it a bug that gedit assumes a working desktop environment, being written to fit a particular desktop environment?

Why does it start at all if that particular desktop environment seems to be missing? In the "root"-case: try to drop privileges, else quit? I can't see how this behavior is part of the design (thus I'll still call it a bug).

> **Quackers said:**
> It still worked 4 days ago

It's more likely that those warnings were suppressed back then and now got enabled (after all, we are using a development release where warnings are of importance ;)).

---

### Post by drs305 on 2010-11-28
I've read this thread and as a frequent user of "gksu gedit" I wanted to see what was happening.

I installed the daily build of Natty, ran 'gksu gedit' and got the same errors as *Quackers*. Even with the messages, the root-owned file saved and reopened correctly despite the terminal messages. 

I could not create the *recently-used.xbel* file using "sudo touch...".

I then installed *nautilus-gksu*. (Edit: You may need to reboot or logout/login before this option will be displayed). I opened the /etc/grub.d folder as administrator by right clicking the folder and choosing that option, edited 10_linux by clicking on it and opening with 'text editor' and saved the file. This being a completely GUI operation, I never saw any warning messages.

Next I inspected /root/.local/share and there was *recently-used.xbel*.

At some point I rebooted, then ran the "gksu gedit" command again. Voila, no error messages in the terminal of any sort.

I'm posting for several reasons, among them one way to create the *recently-used.xbel* file and rid the error messages, and also so someone would confirm the same happens for them.

---

### Post by Quackers on 2010-11-28
Thanks for the info drs305.
I have done what you have done and on looking in the /root folder there is a .recently-used.exbel file, but it is in the root folder. There is no .local folder!

Oddly /local isn't there, but .recentlyused.exbel is in the root folder!

Would it be safe for me to put that file in a folder I create called .local?

---

### Post by Penguin=) on 2010-11-28
Create your new directory so it does not  have error, only becuase you have a error becuase it has either been deleted or you have corrupted it by accident, sorry my friend.

---

### Post by MacUntu on 2010-11-28
> **Quackers said:**
> Would it be safe for me to put that file in a folder I create called .local?

No, that's a different file. Just ```
sudo mkdir -p /root/.local/share
``` and gedit will shut up.

---

### Post by Quackers on 2010-11-28
> **MacUntu said:**
> No, that's a different file. Just ```
sudo mkdir -p /root/.local/share
``` and gedit will shut up.


Thanks, that seems to have shut it up :-)
Thanks drs305 too :-)

---

### Post by drs305 on 2010-11-28
Now the question (at least my question) is: Does /root/.local exist until something creates it after the installation? My guess is no, since the only reason I installed Natty and the first command I ran was "gksu gedit".

When I did that, I got the same error messages as Quackers. I didn't look for /root/.local at the time, but I suspect I would have found that it didn't exist for me either.

What I take away from this until someone tells me otherwise is that using "gksu" with a GTK app is fine, it's just that in this case the .local file hadn't been created yet since it was a new install. Whatever would normally have created the .local folder hadn't occurred on the new installation yet.

---

### Post by MacUntu on 2010-11-28
Don't know about /root/.local, but /root/.local/share definitely doesn't exist unless you start a session (and it's the only folder in .local on my systems, so .local probably isn't there too).

---

### Post by Quackers on 2010-11-28
I have 2 Natty installs and .local wasn't present on either system, so, not a user problem then.

I'll mark the thread as solved, because the error messages have now gone.
Obviously the "why" still exists though :-)

Thanks for all the help and suggestions.

---

### Post by mc4man on 2010-11-29
You could probably consider this a slight bug.
The previous behavior for the .xbel was to be written to ~/ as a user and /root as root.
Now it appears it goes to ~/.local/share as a user, and conversely to /root/.local/share as root.

By default that dir. doesn't exist, typically created when deleting something as root (move to trash.

---

### Post by Quackers on 2010-11-29
> **mc4man said:**
> You could probably consider this a slight bug.
The previous behavior for the .xbel was to be written to ~/ as a user and /root as sudo.
Now it appears it goes to ~/.local/share as a user, and conversely to /root/.local/share as sudo.

By default that dir. doesn't exist, typically created when deleting something as root (move to trash.

That's obviously the "change" that spawned the error messages.

---

### Post by mc4man on 2010-11-29
Of very minor interest - while looking at noticed the default gedit history of 5 can be adjusted, if desired, in gconf-editor.

---

### Post by seeker5528 on 2010-11-29
> **mc4man said:**
> You could probably consider this a slight bug.
The previous behavior for the .xbel was to be written to ~/ as a user and /root as sudo.
Now it appears it goes to ~/.local/share as a user, and conversely to /root/.local/share as sudo.

Stuff that reads/writes configuration stuff in '~' does so with sudo/gksudo/kdesudo too that doesn't change.

Gksudo/kdesudo set the home for the sudo session to the home of the target user, but when using sudo directly you have to use the '-H' option or else *your* home directory is considered to be the home directory for the session.

The home thing isn't the only difference between using gksudo/kdesudo and using sudo directly, but doing 'sudo something' instead of 'sudo -H something' would most commonly be the thing that causes problems for people when something no longer works when run normally because it needs to write/write to a file/directory that is now owned by root.

Later, Seeker

---

### Post by mc4man on 2010-11-29
> **seeker5528 said:**
> Stuff that reads/writes configuration stuff in '~' does so with sudo/gksudo/kdesudo too that doesn't change.

.ect. ect.
Not understanding what your point is, my reference to 'sudo' was in context to this thread, - gksudo gedit, not sudo gedit and to the cause of the warning that previously didn't occur

---

### Post by seeker5528 on 2010-12-01
> **mc4man said:**
> Not understanding what your point is

The point is sudo and gksudo operate a little differently so saying sudo when you mean gksudo is not a good thing. If you had said gksudo instead of sudo I wouldn't have worried about the rest since most people probably don't care about the details, but since software that writes to $HOME always writes to $HOME no matter what the context is and it's $HOME that is changed it becomes relevant how that is handled when switching between sudo and gkudo/kdesudo.

Later, Seeker

---

