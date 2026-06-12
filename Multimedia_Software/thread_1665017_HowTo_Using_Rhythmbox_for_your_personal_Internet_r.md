---
title: "HowTo: Using Rhythmbox for your personal Internet radio station"
date: 2011-01-11
forum: Multimedia Software
---

### Post by unimatrix on 2011-01-11
[SIZE="5"]Goal[/SIZE]
Using Rhythmbox to stream your music to multiple potential listeners over the Internet. But mostly, writing down how I did it so I don't have to re-do all the research the next time.

[SIZE="5"]Steps[/SIZE]
[LIST=1]
[*]Install **icecast2**: [APT link]("apt://icecast2")
[*]Edit **/etc/icecast2/icecast.xml** to configure your password at least. You need to add a user-specific password for the username that will be running Rhythmbox. For example, if your username is *john* you need to put
> <john-password>ChangeThisPassword</john-password>
between the *<authentication> ... </authentication>* tags.
I also suggest you set the **port** to 8000.
[*]Restart icecast2 using the following command:
```
sudo /etc/init.d/icecast2 restart
```
[*]Download the attached script (*shout2send.tar.gz*) and extract it to *~/.gnome2/rhythmbox/plugins/*.
[*]Run (or restart) **Rhythmbox** and click *Edit* --> *Plugins*. Find the plugin called *shout2send* and make sure it is enabled.
[*]In the same window click *Configure...* and set the parameters accordingly (reply to ask me for details if unsure). The important part is to set the **password** and **port** to match the values you've configured in *icecast.xml* in step 2.
[*]That's it. To test it, simply press play. If Rhythmbox freezes then something is probably wrong, and you need to kill it and revise the configuration (or if you give up simply disable the *shout2send* plugin).
[/LIST]

[SIZE="5"]Result[/SIZE]
Provided you did every step in the instructions correctly you should now be able to use a few links:
[LIST]
[*]To access your web radio station: _http://<your-ip>:8000/_
[*]To listen to the stream: _http://<your-ip>:8000/listen_ (This is what people put in Winamp/VLC/WMP to listen to your tunes)
[*]To administer your radio station: _http://<your-ip>:8000/admin_
[/LIST]

[SIZE="5"]Comments and Credits[/SIZE]
I should note that the script available through attachments of this post is a slightly modified version of another script I got from this [blog]("http://www.damonkohler.com/2009/01/rhythmbox-shout2send-plugin.html"). The original script produces an OGG Vorbis stream, which by itself isn't a bad thing, but the problem is that most Windows users won't be able to listen to it without installing some codecs. Thus my script will produce an MPEG Layer III (mp3) stream, which should work on most systems by default.
I hope you find this tutorial useful. If you have any questions/comments don't hesitate to ask.

---

### Post by Lorra on 2011-02-05
Very very nice! Would you know how to avoid the radio from stopping to play on the client every time you hit the next button on Rhythmbox? I mean clients looks like seeing they're playing a playlist with a single song,do you know whether it's possible to let them know about the playlist you're playing in RB?

Thanks in advance.
Lorra.

---

### Post by unimatrix on 2011-02-05
I think this might be specific to some players (VLC perhaps?).
Totem for example doesn't stop playing, but it does have to re-buffer.

It might help to reduce the stream quality, but that's just a bad workaround.

---

### Post by olympus112 on 2011-10-02
I got icecast and installed it. It stopped there i missed something or something happened. I cant do anything with it

---

### Post by dimamali on 2012-06-09
There are not rhythmbox files in the .gnome2 folder anymore. 
The script should be copied to 
```

/usr/share/rhythmbox/plugins/.
```However, it doesn't show up on the plugins list.
Any suggestions?

---

### Post by ugh_bough on 2012-07-06
Hi there,
I also would like to know how to make the plugin show up. I tried both locations. Btw: Im using RB 2.90.1


Thanks
ugh_bough

---

### Post by ugh_bough on 2012-07-06
Ok, the problem is that the .plugin description files are not right and that the plugin uses pygtk which seem to be unsupported now (indicated by [https://bbs.archlinux.org/viewtopic.php?pid=918193](https://bbs.archlinux.org/viewtopic.php?pid=918193) because of a failure message after fixing first issue).


fixed the first issue:
- put plugin into ~/.local/share/rhythmbox/plugins
- move __init__.py into subfolder 'shout2send', i.e. the folder name is ~/.local/share/rhythmbox/plugins/shout2send/shout2send
- rename shout2send.rb-plugin to shout2send.plugin and change header of file content from [RB-Plugin] to [Plugin]

will probably have a look at the second issue. if somebody knows gtk3 and is interested into this plugin... feel free to help us out.
cheers

---

