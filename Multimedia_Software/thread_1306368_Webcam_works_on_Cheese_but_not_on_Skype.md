---
title: "Webcam works on Cheese but not on Skype"
date: 2009-10-30
forum: Multimedia Software
---

### Post by fbugnon on 2009-10-30
Hello,

My **webcam** works out of the box with [COLOR="Red"]**Cheese**[/COLOR], but not with [COLOR="Red"]**Skype**[/COLOR].

Under [COLOR="Red"]**Skype**[/COLOR], when I go to Options > Video and push "Test" button it only show colourful static.

I have tried the solution proposed in [this]("http://ubuntuforums.org/showthread.php?t=993262&highlight=vide+skype+cheese") thread 
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```but it didn't work for me.

My webcam is a NGS detected by [FONT="Courier New"]lsusb[/FONT] as
[FONT="Courier New"]Bus 002 Device 002: ID 0ac8:305b Z-Star Microelectronics Corp. ZC0305 Webcam[/FONT]

I'm running Karmic Koala (9.10) 64bits, with all updates, on a Intel Celeron 450 @ 2,2Ghz and a 82G33/G31 Express Integrated Graphics Controller.

I was wondering if someone else is facing this same problem and if a solution was already found.  Suggestions are also welcome!

Any help appreciated :)

Thanks!

---

### Post by Johndo1 on 2009-10-30
I have the same exact problem with my quick-cam connect. Hopefully someone can find a solution. I saw a thread on the Skype website about this but they didn't figure it out. (I guess it was the Skype website.)

---

### Post by fbugnon on 2009-10-30
Forgot to say I' using the _last available version_ of [COLOR="Red"]**skype**[/COLOR], which is: [FONT="Courier New"][SIZE="3"]Beta 2.1.0.47[/SIZE][/FONT]

---

### Post by Johndo1 on 2009-10-30
So nobody knows what the problem is?

---

### Post by Quespan on 2009-10-31
You could try to add this line in you Skype.sh script
I don't remember where I found it and why it works but it works for me on two laptops.

```
export XLIB_SKIP_ARGB_VISUALS=1
```

---

### Post by habib_seif on 2009-10-31
I have the same problem in Karmic...

The history: 
In Intrepid, when I used the script "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype" the problem was solved completely.

In Karmic, when I use the above script, the webcam can capture motions but in very poor quality.
For example, in the attachment, the skype window is shown when the webcam was capturing a text document. You can see how poor the quality is.

Also, "export XLIB_SKIP_ARGB_VISUALS=1" command didn't solve the problem

Cheers,
Habib

---

### Post by fbugnon on 2009-10-31
Searching the web I found [this page]("http://setdosa.blogspot.com/2009/01/fixing-green-screen-for-skype-video-on.html") explaining how to make it work, but that was with 8.10, so I'm not sure it will work for us.

Anyway, it's a bit more complete than just using [FONT="Courier New"]LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.real.[/FONT] Here what's suggested:   
> 
1. Added

    deb [http://ppa.launchpad.net/lool/ubuntu](http://ppa.launchpad.net/lool/ubuntu) intrepid main
    deb-src [http://ppa.launchpad.net/lool/ubuntu](http://ppa.launchpad.net/lool/ubuntu) intrepid main 

to my sources (/etc/apt/sources.list)

1.5 Update: To import the key, do the following

    gpg --keyserver subkeys.pgp.net --recv-keys CA5D96E9AB82B686 && gpg --export --armor CA5D96E9AB82B686 | sudo apt-key add -


2. Did sudo apt-get update && sudo apt-get upgrade. You should see libv4l-0 get upgraded.

3. Edited my ~/.Skype/<username>/config.xml to add the Video element. Mine did not have a <Video> element, I put it under <Lib> (found it by another round of googling)

    ...
      <Lib>
         ...
         <Video>
          <CaptureHeight>480</CaptureHeight>
          <CaptureWidth>640</CaptureWidth>
          <RecvPolicy>callpolicy</RecvPolicy> 

        </Video>
        ...
      </Lib>
    ...

4. sudo mv /usr/bin/skype /usr/bin/skype.real
5. sudo vi /usr/bin/skype and put the following inside

    #!/bin/bash
    LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.real

 If you use 64 bit then replace with

    #!/bin/bash
    LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype.real

 6. Test your skype video. It should work now. In case it is showing B&W and you are using a Phillips model webcam or a webcam that uses the phillips driver then do the following

7. sudo apt-get install setpwc

8. setpwc -x and you are now set 

I'm not at work so I cannot test it on my computer that has this problem.  Has any of you already tried this?

---

### Post by habib_seif on 2009-10-31
Dear fbugnon,

The only difference between our configuration and the configuration you said is to add some lines to config.xml of Skype.

I added these lines and unfortunately it didn't solve the problem...

Habib

---

### Post by lian1238 on 2009-10-31
> **Quespan said:**
> You could try to add this line in you Skype.sh script
I don't remember where I found it and why it works but it works for me on two laptops.

```
export XLIB_SKIP_ARGB_VISUALS=1
```
thank you so much! it works!

---

### Post by boom2k1 on 2009-11-01
For those that don't work, try following 
1. hansdegoede's instruction on installing  libv4l and another in his instruction..
[http://hansdegoede.livejournal.com/7622.html](http://hansdegoede.livejournal.com/7622.html)

and 

2. install the skype not from medibuntu instead of the skype from skype.com
(there are tons of articles out there in the forum to help with medibuntu package - I got it from ubuntu-tweak [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/))

  : in my case, it didn't work even after applying #1. However, as soon as I uninstalled my original version of skype using sudo apt-get remove skype  
and install medibuntu's skype, the video works!


I probably repeat myself there:
[http://ubuntuforums.org/showthread.php?p=8211716&posted=1#post8211716](http://ubuntuforums.org/showthread.php?p=8211716&posted=1#post8211716)

---

### Post by habib_seif on 2009-11-01
Thanks boom2k1 for the suggestion but even after installing v4l and skype from medibuntu the problem still exists....

Does anyone else have experience about the instructions introduced by boom2k1?

---

### Post by nerdy_kid on 2009-11-02
I have this issue to; i am borrowing a friends webcam, works perfect with cheese but not with anything else.

The camera is a cheapy Gigaware from radioshack, sorry dont know any more specs.

Running Karmic 32bit
NVIDIA drivers

---

### Post by fbugnon on 2009-11-02
Thanks a lot boom2k1!

> **habib_seif said:**
> Does anyone else have experience about the instructions introduced by boom2k1?

Yes, I tried first just downloading and installing the libv4l as per boom2k1's instructions but, even after restarting the computer, the "standard" version of skype would only show the green screen.

Then I removed skype (I was surprised to see that "[FONT="Courier New"]sudo aptitude remove skype[/FONT]" worked even though I had installed via .deb package).

Then I downloaded the mediabuntu skype packages ([FONT="Courier New"]skype-common[/FONT] and [FONT="Courier New"]skype[/FONT]) and installed them.

Now my very cheap NGS webcam works on both Cheese and Skype.

Hope this can be helpful to others too. :)

PS: should I mark question as SOLVED?

---

### Post by habib_seif on 2009-11-03
I think that tagging the thread as SOLVED is so soon...

I tried to install v4l and skype from medibuntu, but my problem still exists :-(

As I said before, I think that the problem is Karmic related. Because the skype from skype.com worked with my webcam without any problem in older versions of ubuntu.

Thanks,
Habib

---

### Post by habib_seif on 2009-11-04
Dear friends,

My problem with my webcam also fixed ;)

Karmic required not only installing skype from medibuntu, but also required adding 
```
  
  <Video>
    <CaptureHeight>480</CaptureHeight>
    <CaptureWidth>640</CaptureWidth>
    <RecvPolicy>callpolicy</RecvPolicy>
  </Video>

```
to the end of ~/.Skype/habibseifzadeh/config.xml file before </config> tag.

By the way, creating a wrapper file with 
```

#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l1.so /usr/bin/skype

```
or something similar is not required. Because skype from medibuntu itself has such file...

Cheers,
Habib

---

### Post by fbugnon on 2009-11-04
@habib_seif, great to hear you could also find your *bonheur*!

So, I think we were all able to fix this issue.

Thanks a lot for all of you who participate and help solve others' problems.

Thread mark as SOLVED!:p

---

### Post by relic70 on 2009-11-08
> **habib_seif said:**
> Dear friends,

My problem with my webcam also fixed ;)

Karmic required not only installing skype from medibuntu, but also required adding 
```
  
  <Video>
    <CaptureHeight>480</CaptureHeight>
    <CaptureWidth>640</CaptureWidth>
    <RecvPolicy>callpolicy</RecvPolicy>
  </Video>

```
to the end of ~/.Skype/habibseifzadeh/config.xml file before </config> tag.

By the way, creating a wrapper file with 
```

#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l1.so /usr/bin/skype

```
or something similar is not required. Because skype from medibuntu itself has such file...

Cheers,
Habib

Sorry Habib - it didn't work for me

---

### Post by fbugnon on 2009-11-09
> **relic70 said:**
> Sorry Habib - it didn't work for me

Have you try installing libv4l (as per boom2k1 instructions) and getting skype from medibuntu sources?

(Those are the steps that worked for me, even though differing a little from those that worked for habib_seif)

---

### Post by strimmer1 on 2009-11-12
Thanks for the help. My Creative Tech VF0250 works in Karmic.  
1 Added Medibuntu sources

[LEFT] [FONT=Courier New][SIZE=2]sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list  --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update[/SIZE][/FONT]
[/LEFT]
 
2 unloaded Skype as directed above

[FONT=Courier New][SIZE=2][COLOR=black]sudo aptitude remove skype[/COLOR][/SIZE][/FONT]

3 Then I downloaded the mediabuntu skype packages ([FONT=Courier New][SIZE=2]skype-common[/SIZE][/FONT] and[SIZE=2] [/SIZE][FONT=Courier New][SIZE=2]skype[/SIZE][/FONT]) and installed them, with Synaptics Package Manager {from the Medibuntu site}. Didn't work until I rebooted.

4 Seems to work with Ekiga and Cheese if you quite Ekiga Skype first.

---

### Post by zi99y on 2009-11-14
I have a Sweex cheapo webcam, when I was using Karmic 32bit it worked with the official deb off the skype site, but since installing 64bit Ubuntu I get the green corruption.

Uninstalling Skype and reinstalling from the Medibuntu repository has fixed this now. 

It's worth noting however, that the video quality is atrocious compared to using skype on windows.

---

### Post by relic70 on 2009-11-14
> **fbugnon said:**
> Have you try installing libv4l (as per boom2k1 instructions) and getting skype from medibuntu sources?

(Those are the steps that worked for me, even though differing a little from those that worked for habib_seif)

Turns out my problem was that Cairo Dock when running conflicted with Skype. Found something about that in the Cairo Dock forums. I logged in with Cairo Dock disabled from starting and Skype worked perfectly for me.

Seems there's alot of program conflicts and the like floating around.

---

### Post by ziogelis77 on 2010-01-11
I am using Karmic 32bit and Skype from medibuntu repositories.

In my case I had to edit the file /usr/bin/skype because the LD_PRELOAD variable in that file pointed to a non-existent file 

/usr/lib/libv4l/v4lcompat.so

while the existing file was 

/usr/lib/libv4l/v4l1compat.so

so, if for some it all fails, check this file!

sudo nano /usr/bin/skype
```
#!/bin/sh
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so  /usr/bin/skype.real "$@"
```

---

### Post by primo6711 on 2010-03-10
can you explain how to do this for a newbie... like what to click how to open etc.... thank you

---

### Post by primo6711 on 2010-03-10
karmic 32bit also

---

### Post by lian1238 on 2010-03-10
> **primo6711 said:**
> can you explain how to do this for a newbie... like what to click how to open etc.... thank you

First, see if this works:

Close skype.
Open a terminal: (Applications->Accessories->Terminal)
Copy and paste (right-click, paste) the following into the terminal:
```

export XLIB_SKIP_ARGB_VISUALS=1
skype

```

Try the webcam. If it didn't work, tell me.
If it did, continue:

Close that terminal and open a new one.
Type in the following, enter your password when prompted:
```

sudo mv /usr/bin/skype /usr/bin/skype.real
sudo gedit /usr/bin/skype

```

Now the text editor should appear.
Copy and paste the following into it:
```

#!/bin/sh

export XLIB_SKIP_ARGB_VISUALS=1
skype.real

```
Save it.
In the terminal, type this:
```

sudo chmod a+x /usr/bin/skype

```

Now, you can run skype the normal way.

---

### Post by finlandia99 on 2010-03-18
thanks lian.
but it didn't work for me :(

---

### Post by finlandia99 on 2010-03-19
can someone please explain the [boom2k1]("http://ubuntuforums.org/member.php?u=118963") steps for a newbie

thanks a lot!

---

### Post by tony_all on 2010-03-27
Hi all!

I had the same issue than fbugnon (the colourful static). I'm running Karmic 32bits and
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
solve it! I'm using Skype 2.1.0.81.

Hope this can help.

Cheers

---

### Post by Payteer on 2010-04-20
wait for lucid as both the cam and audio work in skype with no problems, the first time ever, I am loving Lucid.

---

### Post by Dragonbite on 2010-04-20
> **Payteer said:**
> wait for lucid as both the cam and audio work in skype with no problems, the first time ever, I am loving Lucid.

That's good news, since it alsmost seems like support is getting worse, not better.

---

### Post by faisalijaz77 on 2010-06-06
i haved added below code in skype icon command line in properties.
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype 
attach screen shot will help you to understand the error. 
Please any one help on this what action is required.

---

