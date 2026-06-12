---
title: "cant pay streamed videos"
date: 2009-11-05
forum: Multimedia Software
---

### Post by yanvolking on 2009-11-05
Hello Community,

When I open up a web page with links to streamed media (such as YOUTUBE), when I click on the window holding the media, I just get a big black rectangle.  If I click on the big black rectangle nothing happens (the message on the task bar at the bottom is "DONE"). In UBUNTU I use Firefox.

On the same computer, running under windows with Internet explorer everything works fine.

I have installed Adobe Flash Media player, and toyed around with others, but the result is always the same.

Any ideas what the problem could be?

Thanks

---

### Post by dvlchd3 on 2009-11-05
Open Synaptics, search for 'gstreamer'

install all packages that start with gstreamer.  You can only select a few at a time, but it will fail if you attempt to select EVERY gstreamer package, and then mark to install.  (Hope that makes sense)

If it still doesn't work, can you post the output of 'about:plugins' (without quotes) in Firefox.

---

### Post by yanvolking on 2009-11-05
Hi,

Thanks for the hint.  I did everything you said but the problem still persists.  I did not understand the bit about 

copying "the output of 'about:razz:lugins' (without quotes) in Firefox".  Can you be more specific?

Thanks

Yan

---

### Post by michy99 on 2009-11-05
I think dvlchd3 means to type this in the address bar in firefox and press enter:```
about:plugins
```This will show you a page with all your plugins listed.

---

### Post by lovinglinux on 2009-11-05
See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by yanvolking on 2009-11-06
Hi Guys,

Thanks for your help.  The answer to the problem was found in :

See **Solution** [*[COLOR=Red]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR=DarkRed]Firefox optimization and troubleshooting thread[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004").

Basically there exists loads of video streaming applications.  Apparently it's not difficult for too many to be installed then they sort of counter each other.  Best thing then if you have the problem I had is to remove all of them and then load the right one only.

Yan

---

