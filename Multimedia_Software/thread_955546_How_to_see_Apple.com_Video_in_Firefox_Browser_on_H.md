---
title: "How to see Apple.com Video in Firefox Browser on Hardy Heron ?"
date: 2008-10-22
forum: Multimedia Software
---

### Post by send4m3 on 2008-10-22
Hi... everyone... I found interesting article that _Phyrewall_ manage to see apple website movie via gecko in Firefox 3.0.x. I found myself have been installed gecko from apt-get install gecko (I used hardy heron version), and I can't see the latest video from apple.com.

After I checked from about: plugins my gecko installed is Gecko Media Player 0.6.0. I already download the latest gecko media player 0.8.0 that I hope can see apple website video , but I have difficulty to upgrade my gecko. Can you help me  ? Please send acknowledgement to my email in [email]send4m3@yahoo.com[/email] too...

Thank you in advance
steven

---

### Post by Teamgeist on 2008-10-22
Install the package ubuntu-restricted-extras via Synaptic Package Manager or with ```
sudo apt-get install ubuntu-restricted-extras
``` This will pull the nessesary codecs (and some other stuff that will make your life easier) for you.

also have a look at [www.medibuntu.org](www.medibuntu.org) afterwards.

---

### Post by send4m3 on 2008-10-22
Thank you to give me good advice TeamGeist, but it did not solved my problem yet.

---

### Post by Teamgeist on 2008-10-22
Have you restarted firefox?

---

### Post by wolfen69 on 2008-10-22
are you talking about apple movie trailers? if so, the only way i've got them to work is: when you go to click the quality of video (large, medium, small, etc.) *right click* the one you want, and select copy link location. then open vlc. go to file>open network stream>http and paste address. click OK. it seems like alot to do, but you can actually do it pretty quick. hope this helps.

---

### Post by Teamgeist on 2008-10-22
Install the gstreamer0.10-ffmpeg package

```
sudo apt-get install gstreamer0.10-ffmpeg
```

Appletrailers.com works just fine on my machine.

/edit: > are you talking about apple movie trailers? if so, the only way i've got them to work is: when you go to click the quality of video (large, medium, small, etc.) right click the one you want, and select copy link location. then open vlc. go to file>open network stream>http and paste address. click OK. it seems like alot to do, but you can actually do it pretty quick. hope this helps.

This really should not be nessesary.

---

### Post by send4m3 on 2008-10-22
Teamgeist -> I have restarted my firefox, and nothing happen

Wolfen69 -> I dont want to download the film,  I just want to see the Quicktime video on my browser, in this case Firefox 3.0.3

---

### Post by Teamgeist on 2008-10-22
Have you installed the gstreamer0.10-ffmpeg package I mentioned above?

---

### Post by send4m3 on 2008-10-22
I did TeamGeist and it said I have been in newest version, nothing installed, and I restarted my Firefox and nothing happen.. If you type about: plugins in firefox, can u see gecko ? what version you have TeamGeist ? 

Thank you

---

### Post by Teamgeist on 2008-10-22
Alright.

I got it now.

Type (copy and paste) ```
wget -c http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu2_i386.deb

``` in a Terminal (Applications--> Accessories--> Terminal)

This will download the w32codecs package into your home folder.
Double-click on it and install it!

The gecko-Version is not important here. It is a matter of (non-free) codecs.

---

### Post by send4m3 on 2008-10-22
Hi TeamGeist when we go to [http://www.apple.com/macbook/](http://www.apple.com/macbook/) there is some section to click "watch the video" what make me curios is ... QuickTime only give downloadable application for Apple itself and Microsoft, nothing for Ubuntu :) 

I still cant watch the video, always see the text to download the latest QuickTime.

I have been do a wget medibuntu and logout either as your suggest, but nothing happen, same message, download the latest QuickTime, but what to download ?? nothing for Linux ...

---

### Post by Teamgeist on 2008-10-22
ok... we were talking about different things then.

[http://www.apple.com/macbook/](http://www.apple.com/macbook/)  does not work for me either.

Does [http://movies.apple.com/movies/lionsgate/transporter3/transporter3-tlr2a_h.320.mov?width=320&height=136](http://movies.apple.com/movies/lionsgate/transporter3/transporter3-tlr2a_h.320.mov?width=320&height=136)  work for you?

The macbook video can be seen here: [http://www.youtube.com/watch?v=4RbsvK-neBY](http://www.youtube.com/watch?v=4RbsvK-neBY)

---

### Post by send4m3 on 2008-10-22
I think your [http://movies.apple.com/movies/lionsgate/transporter3/transporter3-tlr2a_h.320.mov?width=320&height=136](http://movies.apple.com/movies/lionsgate/transporter3/transporter3-tlr2a_h.320.mov?width=320&height=136) but don't know yet... still progressing proccess.

but this is not what I want, neither in playing youtube. I just very curious how to make QuickTime work in Ubuntu. lol.

Apple always do something so exclusively, that make me very curious. anyone can help ???

---

### Post by wolfen69 on 2008-10-22
> **Teamgeist said:**
> Install the gstreamer0.10-ffmpeg package

```
sudo apt-get install gstreamer0.10-ffmpeg
```

Appletrailers.com works just fine on my machine.

/edit: 

This really should not be nessesary.

i've tried every codec known to man, and have never gotten firefox to play apple movie trailers. oh well.

---

### Post by Teamgeist on 2008-10-22
> **wolfen69 said:**
> i've tried every codec known to man, and have never gotten firefox to play apple movie trailers. oh well.

Is the w32codecs package from medibuntu.org installed?

---

### Post by gandaran on 2008-10-22
there seems to be some kind of problem playing this url [http://www.apple.com/macbook/](http://www.apple.com/macbook/) with the embedded player plugin, I tried firefox/totem plugin and opera/mplayer plugin, with opera and mplayer plugin I got a black window but could copy the streaming url which  works just fine in stand alone players mplayer and totem, I wonder why does it work in a player but not in the embedded player plugin?

url stream [http://movies.apple.com/movies/us/apple/mac/macbook/2008/designvideo/apple_new_macbook_video_20081014_e320x180.3gp](http://movies.apple.com/movies/us/apple/mac/macbook/2008/designvideo/apple_new_macbook_video_20081014_e320x180.3gp)

---

### Post by send4m3 on 2008-10-22
gandaran -> that make me curious too... I think we have to get embedded player that can play QuickTime new version on Firefox / Opera

---

### Post by wolfen69 on 2008-10-22
> **Teamgeist said:**
> Is the w32codecs package from medibuntu.org installed?

yes.

---

### Post by wolfen69 on 2008-10-22
> **gandaran said:**
> there seems to be some kind of problem playing this url [http://www.apple.com/macbook/](http://www.apple.com/macbook/) with the embedded player plugin, I tried firefox/totem plugin and opera/mplayer plugin, with opera and mplayer plugin I got a black window but could copy the streaming url which  works just fine in stand alone players mplayer and totem, I wonder why does it work in a player but not in the embedded player plugin?

url stream [http://movies.apple.com/movies/us/apple/mac/macbook/2008/designvideo/apple_new_macbook_video_20081014_e320x180.3gp](http://movies.apple.com/movies/us/apple/mac/macbook/2008/designvideo/apple_new_macbook_video_20081014_e320x180.3gp)

*that* url stream works for me in firefox. whoever can get apple movie trailers to work in firefox is a better (or luckier) person than me. i've been trying since the beginning of time. no big deal though. i just copy and paste the url into vlc.

---

### Post by send4m3 on 2008-10-22
wolfen69 -> can u display the movie on firefox ? instead of from vlc player ???

---

### Post by aragorn2909 on 2008-10-22
The easiest solution to this problem, in my estimation, is to remove mozilla-plugin-vlc and replace it with mozilla-mplayer.

---

### Post by gandaran on 2008-10-23
> **aragorn2909 said:**
> The easiest solution to this problem, in my estimation, is to remove mozilla-plugin-vlc and replace it with mozilla-mplayer.

you got it playing with mplayer-mozilla ? I just get a black window! no sound or video, what version of mplayer you have?

---

### Post by aragorn2909 on 2008-10-23
> **gandaran said:**
> you got it playing with mplayer-mozilla ? I just get a black window! no sound or video, what version of mplayer you have?

I should have mentioned...I have the Medibuntu repo enabled, so I have the Medibuntu version.

---

### Post by gandaran on 2008-10-23
> **aragorn2909 said:**
> I should have mentioned...I have the Medibuntu repo enabled, so I have the Medibuntu version.

updated opera to 9.60 and now mplayer plugin can play the url!

---

### Post by send4m3 on 2008-10-23
aragorn2909 -> i have installed mozilla-mplayer packaged , it does not work either.i have installed some part of medibuntu too. but the result is negative. how to know that i have installed the same packaged as yours ? 

gandaran -> i do have opera installed, even in 9.61 version . it doesn't work either.

---

### Post by gandaran on 2008-10-23
send4m3
check if **libquicktime1**, **libfaad0**, **libfaac0** is installed and the w32codecs too

---

### Post by send4m3 on 2008-10-23
gandaran -> thanks for the reply, but how to check it ? can you inform me how to do it ? using terminal ?

have u success to see the video on your browser ? what kind of browser you used ?

thanks

---

### Post by gandaran on 2008-10-24
> **send4m3 said:**
> gandaran -> thanks for the reply, but how to check it ? can you inform me how to do it ? using terminal ?

open synaptic package manager, scroll down to libquicktime1, libfaad0, libfaac0 and the 'medibuntu' w32codecs. if they are not installed mark them for install and click the apply button.
run synaptic update by clicking the reload/refresh button before you do anything there.
I believe those codecs are enough to play apple movies, if I'm wrong I'll try to find out the correct ones.

> have u success to see the video on your browser
yes, but just with opera and mplayer-mozilla plugin, my firefox is set to use the totem-gstreamer plugin and as you know totem will only play the stream link in stand alone player.
you'll have no problem playing on firefox with the mplayer-mozilla plugin
did you remove the totem plugin before installing the mplayer-plugin?

---

### Post by send4m3 on 2008-10-27
gandaran -> i have installed the necessary files as you mention above. i try on opera, the result is negative. how to know my operan use mplayer-plugin instead of totem ??? if i dont have mplayer-plugin on my opera , how to installed that plugin ? thx

---

### Post by gandaran on 2008-10-27
> **send4m3 said:**
> gandaran -> i have installed the necessary files as you mention above. i try on opera, the result is negative. how to know my operan use mplayer-plugin instead of totem ??? if i dont have mplayer-plugin on my opera , how to installed that plugin ? thx

opera is a kde browser doesn't work with gtk apps (totem), you just remove toten-mozilla plugin and install the mozilla-mplayer plugin, use synaptic for that, this is the easy way, mplayer now works in both browsers
getting browsers to use deferent plugins is a bit more complicated, just remove the totem plugin not the player so that mplayer can work.

---

