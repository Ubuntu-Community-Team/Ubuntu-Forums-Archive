---
title: "A Movie Player"
date: 2007-04-16
forum: Multimedia &amp; Video
---

### Post by gunthermeyer on 2007-04-16
I'm looking for a really good dvd movie player for Ubuntu 6.10. I've tried Totem and it didn't work and then I tried Move Player and it didn't work. Any other players out there.

---

### Post by 67GTA on 2007-04-16
One of them should have worked. You might need to install some codecs or configure the players. Why didn't they work? Did you get any error messages?

---

### Post by RomeReactor on 2007-04-16
Hi. [UbuntuGuide]("http://ubuntuguide.org") is a very good place to sort out many of the more common problems associated with enabling multimedia for our system. To enable DVD playback in Edgy, [go here]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_DVD_playback_capability"); for Dapper, try [here]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_install_DVD_playback_capability"). [This link]("http://ubuntuguide.org/wiki/Ubuntu#How_to_install_DVD_playback_capability") is for Breezy.

---

### Post by gunthermeyer on 2007-04-16
It goes through the motions of starting up the movie and I get as far as the startup sceen and thenit abruptly stops and gives an error. It tells me that I'm trying to play a dvd disk that is encrypted ant then it tells me that I need a libdvdcss to run the movie. Last night I ran a regionset command from the terminal window and it still didn't work. I can't seem to find the libdvdcss file. I rebooted after I had ran the region settting and I also just ran it straight without rebooting and still no luck. There has to be a way to set the region setting preference to make it run. I'm using Ubuntu 6.10. My computer is a Dell 600m and the dvd player is the one that came with the computer. Any more info would be nice.

---

### Post by 67GTA on 2007-04-16
Look in the Synaptic package manager and see if libdvdcss is installed. libdvdcss doesn't require you to have the region set,

---

### Post by gunthermeyer on 2007-04-16
No, libdvdcss isn't there. I've even checked a third party one called automatix2 and still no luck. Any other suggestions. I  would really like to get this dvd movie player to work.

---

### Post by RomeReactor on 2007-04-16
Do you have the Medibuntu repositories? Open a terminal and enter

```
gksudo gedit /etc/apt/sources.list
```

and look for this entry:

```
## PLF REPOSITORY (Unsupported. May contain illegal packages. Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
```

Add it if it's not there already, save the file and close Gedit; now open Synaptic and press the **Reload** button on the top left. After it finishes reloading the package information, search for **libdvdcss** and install it. When that's done, open a terminal and enter

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

Also make sure you have **totem-xine** instead of **totem-gstreamer**

```
sudo apt-get install totem-xine libxine1 libxine-extracodecs
```

---

### Post by 67GTA on 2007-04-16
You have to add the medibuntu repository. Use the link and just copy the PLF medibuntu entry to your /etc/apt/sources.list. Be sure to do the final step and get the key for the repositories. The steps are pretty clear, so just be sure to read before you start.

---

### Post by gunthermeyer on 2007-04-16
Hey man it worked. thanks a lot. Now is this going to work after I turn off my computer?

---

### Post by RomeReactor on 2007-04-16
It _should_ work; it's not a volatile setting. I haven't experienced any problems after installing it, if that's any indication. :D

---

### Post by dreadlord_chris on 2007-04-17
> **gunthermeyer said:**
> Hey man it worked. thanks a lot. Now is this going to work after I turn off my computer?

No....



you'll have to turn your computer back on before it will work again :twisted:

---

### Post by kila kila kila on 2007-04-17
Hi.  When I get to this step:

```
sudo /usr/share/doc/libdvdread3/install-css.sh
```

I get:

```
sudo: /usr/share/doc/libdvdread3/install-css.sh: command not found
```

I know I'm not doing something right.  Just can't figure out what.

libdvdcss2 and libdvdread3 are both marked as installed in Synaptic.

I'm on 6.06.1.  Any help would be appreciated.

---

### Post by 67GTA on 2007-04-17
Have you tried playing a movie again since you installed them?

---

### Post by kila kila kila on 2007-04-17
Yeah.  Even rebooted.  Still getting the same error re: encryption.

Also, when I search in Synaptic for the Medibuntu repository you mentioned earlier, I don't get any results.  Could this have something to do with it?

---

### Post by RomeReactor on 2007-04-17
Hi. On Dapper the correct path is

```
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
```

---

### Post by jesterpezz on 2007-04-17
can i post a question here about Mplayer? or do i need to go somewhere else?
im running Dapper.

thx

jesse

---

### Post by RomeReactor on 2007-04-17
Go ahead, though you're likely to get more answers in a new post; just make sure you search the forums first in case someone has already had the same problem as you and solved it. And welcome! :KS

---

### Post by jesterpezz on 2007-04-17
i got it.. i was having trouble with dependencies.. liba* but reloaded the repositories and was able to get it. although any video player i use video dissapears while i move the window, then re-appears when i let it go.. i am running AIGLX w/ compiz cube.. everything works fine except when i move a window or rotate the box, video goes away till i let it go. then its fine again.
hope you can help i will look around at other posts but so far i dont see anything w/similar problem.

jesse.....

---

### Post by jesterpezz on 2007-04-18
> **RomeReactor said:**
> Go ahead, though you're likely to get more answers in a new post; just make sure you search the forums first in case someone has already had the same problem as you and solved it. And welcome! :KS

oh.. THANKS for welcoming me! :D .. im not much of a thread person but i am totally nerding out for the past month on ubuntu and pretty much figured everything out by reading and going to all these threads and reading everyones posts. but just a few things are twisting my brain like the video not showing when i move the window around. also getting the 3D plugin to work on compiz so it looks like the pages are layered instead of flat. just stuff like that.:confused: 

jesse....

---

### Post by RomeReactor on 2007-04-18
> **jesterpezz said:**
>  ...pretty much figured everything out by reading and going to all these threads and reading everyones posts.

Yeah, same here. These forums have *many* knowledgeable people; any problems I've had were solved by searching and reading their posts! Sorry I can't be of help on your Compiz issue, though...

---

### Post by jesterpezz on 2007-04-18
> **RomeReactor said:**
> Yeah, same here. These forums have *many* knowledgeable people; any problems I've had were solved by searching and reading their posts! Sorry I can't be of help on your Compiz issue, though...

no problem.. at least i have a good idea now of what i am looking for and i am now active on these threads.. thanks for the warm welcome again!:) 

jesse...

---

### Post by MichaelSM on 2007-04-18
Hi. My name is Michael. Curse me if you like. Ubuntu Edgy at this stage is my preferred OS. Thanks to various people on the Web like MacEwan and Dave Shuck, I have a happy Edgy with no printer problems, Bluetooth going like a pearler with a Nokia 6233, Frostwire up and running with Sun Java 6 you name it. Fine. Thanks to all, and thanks to me for following thousands of threads to find the right ones. It just takes a lot of time at first.
Regarding M-Player and Totem. All distros are different. I set up a computer for my Mum a year or so ago with Mandriva 2006. Even back then, Mandriva with Gnome desktop, Totem played just about everything on Earth including wmvs and avis. I often wonder why I switched distros. Well , why not? I'm not married yet ...

OK back to media players. Mephistopheles might disagree, but I have no media gods, even him/her. I've fiddled with M-Player downloads to make it work, and what a waste of time.Forget it.

Download VLC player for Linux. Look it up on Google. 

I just simply gave up with frigging around with MPlayer particular downloads which never seemed to work .

VLC will play just about anything with knobs on it. Just watch out when you install it. Don't just go Enter>Enter like a dill. It doesn't carry much spy-ware but anything is possible at 11.00 pm. 

I hope my language hasn't upset anyone. I'm just a realist. I must have spent 20 hours or so(which makes me incredibly STOOPID) trying to get MPlayer and you name it to play wmvs. Just a very long learning curve which came to an abrupt and sensible end.

Cheers, Mike.

Look up VLC Media Player (Video Lan Client) and download its player, and forget all your worries. VLC plays just about anything. I don't know where they make their money but just about every codec in history is supported, and it's free. Just be vigilant with priorities, becos VLC will insinuate itself into your system. Be careful when you check or uncheck boxes on download, that's all. It's all written in plain English, so just don't go Enter>Enter through laziness; there's always something you don't want which can slip by. All you want is the bare essentials, and they're better than anything else I can find.

The Ubuntu community is a fantastic group of people, but covering so many areas of demand something is always gonna slip through the cones

---

### Post by MichaelSM on 2007-04-18
Sorry to reply to my own comment . I just had a look at [http://ubuntuforums.org/showthread.php?t=411262](http://ubuntuforums.org/showthread.php?t=411262) and I'll see if it helps. Cheers, Mike.

---

