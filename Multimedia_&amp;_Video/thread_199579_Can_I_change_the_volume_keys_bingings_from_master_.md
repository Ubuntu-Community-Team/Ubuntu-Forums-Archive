---
title: "Can I change the volume keys bingings from master channel to PCM?"
date: 2006-06-19
forum: Multimedia &amp; Video
---

### Post by Sammi on 2006-06-19
I have the annoying problem that the master channel doesn't really act right. It doesnt' effect the volume of all other channels. 

Especially the master channel doesn't effect the volume of headphones and the mono channel, which I want to be active because it gives better bass.

But I doscovered that the PCM channel does effect the volume of all output channels. Because of this I want to change the key bindings of my volume control buttons from the master channel to the PCM, but I can't figure out how.

I found [another tread]("http://ubuntuforums.org/showthread.php?p=1155376#post1155376") where other people are experiencing the same problem, but they found no fix. So this is a plea to someone who dows know how to fix this to step forward and help the community. Please help us!

Oh and I'm using a Dell Inspiron 9300 laptop.

---

### Post by Sammi on 2006-06-20
I know that noone has answered this question before, because I have tried to search for it. Because of that, I don't think it is wrong, of me to try to pull this tread back up to the first page.

---

### Post by Sammi on 2006-06-20
Oh and is this actually the right room to post this tread in, as it's really a question of key bindings rather than a real audio question?

Where could be a better place to post?

---

### Post by darkcele on 2006-06-21
I've got the same problem.. anyone has got a solution?

---

### Post by patrick295767 on 2006-06-21
[QUOTE=Sammi]I know that noone has answered this question before, because I have tried to search for it. Because of that, I don't think it is wrong, of me to try to pull this tread back up to the first page.[/QUOTE]
 
It might help you (not sure) : 
```
################# multimedia keyboard (define your keys) ###
apt-get -f -y install keytouch
apt-get -f -y install keytouchd 
```
  For changing other bindings, In my case, it's very easy, I use fvwm desktop.

---

### Post by Sammi on 2006-06-22
Dang I'm just going on holliday for more than two weeks, so it's going to be some time before I'm going to be able to test that little application.

But I'l get back to you then. Thanks for the suggestion! :D

---

### Post by zeus77 on 2006-06-23
This fix mentioned in [launchpad]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/41015") might help...

---

### Post by Sammi on 2006-08-04
Hello again. Long time no action on my side. Actually I forgot about this tread.

Launchpad did not fix my problem, so I decided to try keytouch and got this:

$ sudo apt-get -f -y install keytouch
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package keytouch

$ sudo apt-get -f -y install keytouchd
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package keytouchd

... and I have a lot of repositories active.

So I did a Google search for it and found this: [http://prdownloads.sourceforge.net/keytouch/keytouch_2.1.4-0ubuntu1_i386.deb?download](http://prdownloads.sourceforge.net/keytouch/keytouch_2.1.4-0ubuntu1_i386.deb?download)

It's complicated... I'm still figuring it out...

---

### Post by Sammi on 2006-08-04
I found a workaround! :D

I got keytouch to work. You need to get the keytouch-editor too. Get the newest beta version of the editor - it works fine. Just read the documentation on the site and it's all fairly easy actually.
You'll find it all here: [http://keytouch.sourceforge.net/download.html](http://keytouch.sourceforge.net/download.html)

I wasn't able to change the behavior of the volume buttons, but what I did in stead was to remap my stop-, previous-track-, and next-track- mediabuttons to these commands:
[I] amixer sset PCM mute
amixer sset PCM 1- unmute
amixer sset PCM 1+ unmute[/I]

I wasn't using those buttons anyway.

This means I now have control over my PCM channel via my media buttons! :D
Only drawback is that I don't get the visual thingy that shows what level the volume is, but I can live without.

---

### Post by TMU on 2006-09-15
I have the same problem with Master and PCM and would like to use your commands for amixer, but I don't know where to use them.

Did you write them into keytouch?

Regards, TMU

---

### Post by Coutsos on 2006-09-23
I spent a few hours of my morning fussing about this very problem. Luckily I've got a solution. Of sorts. It works, that's all that I'm worried about :)

**Step one:**
Get the keytouch source (don't worry, this is going to be relatively painless)
[source (.tar.gz)](http://prdownloads.sourceforge.net/keytouch/keytouch-2.2.1.tar.gz?download)

**Step two:**
Extract.

**Step three:**
Go to the plugins folder and open "amixer.c" in your text editor of choice. Here's the easiest part: Replace all occurrances of "Master" with "PCM". Bam. You are ~90% done. ([i]Note: if there's some other channel you wish to use, replace "PCM" with the appropriate name).

You should also change the plugin name (I prefer to add a seperate plugin instead of replacing the original). Find the line that says:
> 	{"Amixer", "Marvin Raaijmakers", "GPL 2", "2.2",
And change it to something like:
> 	{"Amixer Modified", "Marvin Raaijmakers", "GPL 2", "2.2",
And, I guess, change the nearby
> "amixer.so",
line to:
> "amixer_modified.so",

Don't forget to save!

**Step four:**
Go back to the main keytouch directory to run these two commands:
```
$ ./configure
$ make
```

When I tried "make install" I got errors about "/usr/local/etc/" not existing. Probably for the best, because I'd rather not have this mess up my already installed ubuntu package.
Now that it's compiled, go to the plugins directory again, and rename "amixer.so" to "amixer_modified.so" (or whatever you decided on).

**Step five:**
```
$ sudo cp amixer_modified.so /usr/local/lib/keytouch/plugins/
```

**Step six:**
Go to System -> Administration -> Keytouch
Under the "Preferences" tab click the "Import..." button, and navigate to /usr/local/lib/keytouch/plugins/" and select the file you just copied there.

**Step seven:**
Back to the "Key settings" tab, configure "Mute", "Volume Up", and "Volume Down" to use the new plugin and appropriate function.

**Step eight:**
Throw a party! (invite please?)

I hope that helps people. When I was looking for how to solve this problem I saw alot of people were struggling with this and didn't come to any solution. In the end, this feature is really not that important (and hardly useful), but I can't deny that I like having it. :razz:

---

### Post by onispawn on 2006-10-04
Here is a keytouch keyboard I made that controls the pcm volume. It works great on my Inspiron 9300, but it should work on anything since its using a simple bash script to access PCM volume settings. Just simply import the file into keytouch and the defaults should work for you needs. You can always change the bash commands a little bit to control what ever you need.

---

### Post by mcgregorandrew on 2006-10-11
> **onispawn said:**
> Here is a keytouch keyboard I made that controls the pcm volume. It works great on my Inspiron 9300, but it should work on anything since its using a simple bash script to access PCM volume settings. Just simply import the file into keytouch and the defaults should work for you needs. You can always change the bash commands a little bit to control what ever you need.


Hi,

I did find that 
amixer sset PCM 1+ unmute
amixer sset PCM 1- unmute

turn the volume up and down, but I can't get keytouch to make any settings take effect.  I can load different keyboards and that all makes sense, but I get messages like this when I start it up:

(keytouch:20008): GLib-CRITICAL **: g_hash_table_lookup: assertion `hash_table != NULL' failed

(keytouch:20008): libgnomevfs-WARNING **: Internal error: the configuration system was not initialized. Did you call _gnome_vfs_configuration_init?

(keytouch:20008): GLib-CRITICAL **: g_hash_table_lookup: assertion `hash_table != NULL' failed

(keytouch:20008): libgnomevfs-WARNING **: Internal error: the configuration system was not initialized. Did you call _gnome_vfs_configuration_init?
keytouchd: no process killed

And this message when I press "Apply":
Warning: Not all keys can be grabbed by this program. This
         can be caused by another program which is already
         grabbing these keys.


when I run keytouch from the keyboard.

Any ideas what is stopping keytouch from working?

---

### Post by VuDu on 2006-11-17
[http://ubuntuforums.org/showpost.php?p=1772934&postcount=8](http://ubuntuforums.org/showpost.php?p=1772934&postcount=8)

> 
[http://gnomesupport.org/forums/viewtopic.php?t=10879](http://gnomesupport.org/forums/viewtopic.php?t=10879)

Looks like it's a know bug.
Too bad they haven't fixed it yet. :(


[http://bugzilla.gnome.org/show_bug.cgi?id=173035](http://bugzilla.gnome.org/show_bug.cgi?id=173035)


---

### Post by qiemem on 2006-12-21
Hey all, definitely the most productive thread on this issue.

Anyway, I, like mcgregorandrew, can't get the changes to take effect. When running keytouch from terminal, I get this when I hit 'apply':
```

Warning: Not all keys can be grabbed by this program. This
         can be caused by another program which is already
         grabbing these keys.

```

Is there a way to disable Gnome's default keyboard shortcut program?

Update:
Heh, just had to restart... Works great now!

---

### Post by ingomueller.net on 2007-01-11
Hi!

I had a similar problem one month ago and have spent a lot of time in its solution. As I stumbled upon this post, probably others will, so I'll post the link to a howto I wrote:

[http://alsa.opensrc.org/How_to_use_softvol_to_control_the_master_volume](http://alsa.opensrc.org/How_to_use_softvol_to_control_the_master_volume)

I hope this helps someone...

Ingo

---

### Post by VuDu on 2007-01-20
[http://ubuntuforums.org/showpost.php?p=2039379&postcount=9](http://ubuntuforums.org/showpost.php?p=2039379&postcount=9)

> **VuDu said:**
> [http://bugzilla.gnome.org/show_bug.cgi?id=173035](http://bugzilla.gnome.org/show_bug.cgi?id=173035)

Check the topic again...
> Comment #36 from Jan Arne Petersen (points: 1
2007-01-08 15:41 UTC [reply]

Created an attachment (id=79756) [edit]
Patch to implement the sound-capplet and keybindings part


Comment #37 from Thomas Wood (control-center developer, points: 15)
2007-01-08 22:40 UTC [reply]

Patch looks generally good - let's get this in got 2.18!


Comment #38 from Rodrigo Moya (control-center developer, points: 21)
2007-01-08 22:55 UTC [reply]

Patch committed

Great news, no?

---

### Post by MarvinR on 2007-01-20
> **Coutsos said:**
> I spent a few hours of my morning fussing about this very problem. Luckily I've got a solution. Of sorts. It works, that's all that I'm worried about :)

In the latest (beta) version of keyTouch it is possible to select the mixer channel that should be used for controlling the volume.

---

