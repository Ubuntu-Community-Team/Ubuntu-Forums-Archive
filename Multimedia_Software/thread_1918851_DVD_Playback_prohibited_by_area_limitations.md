---
title: "DVD Playback prohibited by area limitations"
date: 2012-02-01
forum: Multimedia Software
---

### Post by bluexrider on 2012-02-01
Need to shrink 8.5GB DVD to 4.7GB and burn a DVD with NTSC format. Sounds simple right?

I have tried several ways and combined different apps without success.

The DVD player keeps saying "Playback prohibited by area limitations".

Here is my arsenal of applications

AcidRip DVD ripper

Arista Transcoder, which doesn't work right because of a bug!

Avidmux (GTK)

Bombono DVD

Brasero 

DeVeDe

Dvd95

DVD::Rip

HandBrake

K3B

Nero Linux

WinFF


Please give me some pointers.  Thanks

---

### Post by hansdown on 2012-02-01
Hi, bluexrider.

The dvd player's region code is set to a different region, than the dvd.

```
sudo apt-get install regionset
```

Be careful.  the region can only be set 5 times, then locks.

[http://en.wikipedia.org/wiki/DVD_region_code](http://en.wikipedia.org/wiki/DVD_region_code)

---

### Post by bluexrider on 2012-02-01
I attacked that issue some time ago. The region mask is 0. So, are you saying it should be different?

For the sake of argument...how do you determine the region code of the DVD being copied?

---

### Post by hansdown on 2012-02-01
It should play all regions.

Is this a Sony player?

I googled

```
The DVD player keeps saying "Playback prohibited by area limitations".
```

Sony pops up a lot.

If you open DVD95, can you shrink the disk?

I remove all language subtitles.  They take up a large amount of space.

[http://www.google.com/search?client=ubuntu&channel=fs&q=The+DVD+player+keeps+saying+%22Playback+prohibited+by+area+limitations%22.&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=The+DVD+player+keeps+saying+%22Playback+prohibited+by+area+limitations%22.&ie=utf-8&oe=utf-8)

---

### Post by bluexrider on 2012-02-01
> **hansdown said:**
> It should play all regions.

Is this a Sony player?

I googled

```
The DVD player keeps saying "Playback prohibited by area limitations".
```Sony pops up a lot.

If you open DVD95, can you shrink the disk?

I remove all language subtitles.  They take up a large amount of space.

[http://www.google.com/search?client=ubuntu&channel=fs&q=The+DVD+player+keeps+saying+%22Playback+prohibited+by+area+limitations%22.&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=The+DVD+player+keeps+saying+%22Playback+prohibited+by+area+limitations%22.&ie=utf-8&oe=utf-8)

Funny you should ask, Yes it is. That happens to be the Home Theatre System in which i have the issue. I can play the original, without issues, in the Sony Player. I cannot however play a copy which I have burned. 

Thus we have the problem. I am ready to break out the Broadsword and start hacking at its bowels.  

DVD95- Yes, I can shrink it to 4.3GB

---

### Post by hansdown on 2012-02-01
You "may" find something helpful in this link.

[http://www.google.com/search?client=ubuntu&channel=fs&q=The+DVD+player+keeps+saying+%22Playback+prohibited+by+area+limitations%22.&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=The+DVD+player+keeps+saying+%22Playback+prohibited+by+area+limitations%22.&ie=utf-8&oe=utf-8)

I used to sing the praises of Sony, at one time.  :-$

---

### Post by bluexrider on 2012-02-01
> **hansdown said:**
> You "may" find something helpful in this link.

[http://www.google.com/search?client=ubuntu&channel=fs&q=The+DVD+player+keeps+saying+%22Playback+prohibited+by+area+limitations%22.&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=The+DVD+player+keeps+saying+%22Playback+prohibited+by+area+limitations%22.&ie=utf-8&oe=utf-8)

I used to sing the praises of Sony, at one time.  :-$
Been there, done that....pretty much looked at all those forums and haven't found an answer.

Thanks for your response.

---

### Post by bluexrider on 2012-02-02
Bump for more info. Thanks

---

### Post by hansdown on 2012-02-02
I'm still looking too.

One other thing,is the disc burned to PAL or NTSC format?

---

### Post by bluexrider on 2012-02-03
> **hansdown said:**
> I'm still looking too.

One other thing,is the disc burned to PAL or NTSC format?
I have set the interlace to NTSC

---

### Post by bluexrider on 2012-02-04
Bump for more....

---

### Post by mc4man on 2012-02-04
You may wish to check some things on your problem disk, if so mediainfo could do.
mediainfo isn't in default ubuntu repos, will be in the upcoming 12.04
So the one way to get is use this ppa
[https://launchpad.net/~shiki/+archive/mediainfo/+packages](https://launchpad.net/~shiki/+archive/mediainfo/+packages)

```
sudo add-apt-repository ppa:shiki/mediainfo
```
```
sudo apt-get update && sudo apt-get install mediainfo-gui
```

If so ^, then after installing insert your burned dvd, close out any pop up.

Then open mediainfo, click on the 'Open file' icon or go from menu > File > Open > Open  File(s)
Browse to > File System > media > your disc's name > VIDEO_TS & choose the .IFO for the main movie title. Click open  - screen 1

This will open it in mediainfo's 'Easy' mode. From menu go  View > HTML
You will see some info inc. the standard, (NTSC or PAL), aspect ratio & framerate. 
Confirm that the .IFO reports it is NTSC, with  an ar of 720x480 & typically a frame rate of 29.970 - screen 2

Now also open a 2nd instance of mediainfo or return the current one to "Easy" mode. Then repeat the above but this time open a .VOB from the main movie title, usually listed directly below the .IFO you opened

Again switch to HTML mode & compare, look at the aspect ratio & framerate, though the framerate may show at 23.976 which is typical for NTSC movie content - screen 3

If you wish to copy anything from any of the above switch mediainfo to View > Text

---

### Post by bluexrider on 2012-02-04
mc4man,

Did as suggested and found an issue, which I don't know if its me or the DVD95 application but the height vs width is incorrect....like 720 x 0 . So I need to see if the shrink is the problem or the burning is?

Thanks for you help, It gave me more of a clue to work with. 

Not solved but close.

---

### Post by bluexrider on 2012-02-05
More issues now. Cannot get DVD95 to shrink without using PAL interlace. 

K3B cannot find /tmp/FOLDER, most likely a permissions thing.

Hanbrake doesn't have the correct format.

Avidemux cannot continue has broken pipe.


I give up. This is crazy!

---

### Post by mc4man on 2012-02-05
You gone this far maybe try k9copy - can be a bit obsure at first as to using, I think there's a wizard option for dvd_video

It can handle some titles with structure protection, others it can't
Many times the best option is not the use orig. menus, just reauthor to main movie only

(don't have installed here. back when I did do alot of dvd ripping/burning would just use windows & one prog. to rip, another to do re-encoding using a real mpeg2 encoder like CCE, another to burn. For a while used to run most of those progs thru wine on ubuntu, not much lately

---

### Post by bluexrider on 2012-02-05
Exactly! I just came back to update my findings. 

Installed K9Copy and used K3B OMG! how easy it was.

The wizard worked and it took less time than any other applications I have used. 

It cranked out 2 copies Ripped and burned in less than an hour.

Going to rid my machine of everything else.

MANY Thanks

---

