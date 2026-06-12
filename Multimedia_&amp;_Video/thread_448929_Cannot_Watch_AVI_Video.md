---
title: "Cannot Watch AVI Video"
date: 2007-05-19
forum: Multimedia &amp; Video
---

### Post by Prometheus.172214 on 2007-05-19
I have an avi movie, which a friend ripped and passed over. However, I cannot play it in Ubuntu. The original video file is an official presentation in our office and it was sent as a DVD and just to make it easier for people to carry it along, a coworker ripped it into avi format. Don's ask me how he did it... Anyway, the problem is, I copied it over to my laptop from a network drive where it was shared for everyone and I cannot play it. I tried VLC, Xine, XMMS, Totem and nogo. When I look at the file in the File Manager, it shows me an icon with the file name and the icon looks like a preview thumbnail and I can clearly see that the icon says content blocked. The messed up part being that I have some avi files I got from various torrents and these not so legal files play fine and here is a genuine file that I have which has been ripped just so we can have a lower file size, it does not play...

Please Help.

[IMG]http://img178.imageshack.us/img178/2757/browsepn7.jpg[/IMG]

---

### Post by taurus on 2007-05-19
What happens if you try to play it from a terminal?

```
cd Data
vlc "compUgate 07 present.avi"
```

---

### Post by Prometheus.172214 on 2007-05-19
Ran the Terminal like you said and got these details as is from there 

```
azariath@(none):~/Data
azariath@(none):~/Data vlc "compUgate 07 present.avi"
VLC media player 0.8.6 Janus
[00000286] logger interface: using logger...
[00000288] logger interface: using logger...
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  102
  Current serial number in output stream:  103
pure virtual method called

```

So, what does this mean ?  :confused::(

Anyway, from I side I did a bit of googling and found that using for X 11 VideoOutput fixed this for another guy, so I tried it and no luck. 
Just in case, if this makes any sense, I ran the commadn xvinfo from the same Terminal and got this output.

```

azariath@(none):~$ xvinfo
X-Video Extension version 2.2
screen #0
  Adaptor #0: "Intel(R) Video Overlay"
    number of ports: 1
    port base: 73
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x23
      depth 24, visualID 0x24
      depth 24, visualID 0x25
      depth 24, visualID 0x26
      depth 24, visualID 0x27
      depth 24, visualID 0x28
      depth 24, visualID 0x29
      depth 24, visualID 0x2a
    number of attributes: 10
      "XV_COLORKEY" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 66046)
      "XV_BRIGHTNESS" (range -128 to 127)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CONTRAST" (range 0 to 255)
              client settable attribute
              client gettable attribute (current value is 64)
      "XV_DOUBLE_BUFFER" (range 0 to 1)
              client settable attribute
              client gettable attribute (current value is 1)
      "XV_GAMMA0" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 526344)
      "XV_GAMMA1" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 1052688)
      "XV_GAMMA2" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 2105376)
      "XV_GAMMA3" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 4210752)
      "XV_GAMMA4" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 8421504)
      "XV_GAMMA5" (range 0 to 16777215)
              client settable attribute
              client gettable attribute (current value is 12632256)
    maximum XvImage size: 1920 x 1080
    Number of image formats: 4
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
  Adaptor #1: "Intel(R) Textured Video"
    number of ports: 16
    port base: 74
    operations supported: PutImage 
    supported visuals:
      depth 24, visualID 0x23
      depth 24, visualID 0x24
      depth 24, visualID 0x25
      depth 24, visualID 0x26
      depth 24, visualID 0x27
      depth 24, visualID 0x28
      depth 24, visualID 0x29
      depth 24, visualID 0x2a
    number of attributes: 2
      "XV_BRIGHTNESS" (range -128 to 127)
              client settable attribute
              client gettable attribute (current value is 0)
      "XV_CONTRAST" (range 0 to 255)
              client settable attribute
              client gettable attribute (current value is 0)
    maximum XvImage size: 2048 x 2048
    Number of image formats: 4
      id: 0x32595559 (YUY2)
        guid: 59555932-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)
      id: 0x32315659 (YV12)
        guid: 59563132-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x30323449 (I420)
        guid: 49343230-0000-0010-8000-00aa00389b71
        bits per pixel: 12
        number of planes: 3
        type: YUV (planar)
      id: 0x59565955 (UYVY)
        guid: 55595659-0000-0010-8000-00aa00389b71
        bits per pixel: 16
        number of planes: 1
        type: YUV (packed)

```

---

### Post by taurus on 2007-05-19
And xine doesn't play, either?

```
xine "compUgate 07 present.avi"
```

---

### Post by Timokl on 2007-05-19
Prometheus, AVI is just a container file. It can contain video and sound data encoded with different encoders, like DivX, Xvid to name some more popular choices. It might be a problem that your co-worker used a problematic encoder, or protected the video with some nasty DRM by doing so.

You can check the following way:

Open the file with Vlc.

Choose in the menu View / Stream and Media Info ...

Select the tabe Advanced Info.

There you can find the information about the codecs used.

Also, ask your friend with what programme and with what coded he did encode the avi file.

Hope this helps a bit,
Timo

---

### Post by Prometheus.172214 on 2007-05-19
Taurus : No, Xine also does not work. 

Timokl: I suspected the same before, based on how the screen shot looked. However, I could not pinpoint, the exact cause as the window just flashes away in a second. So, I did some screen recording and guess what you where right....  This looks like a nasty case of DRM........ The message that I could not make out earlier was

CONTENT BLOCKED
The media file can only be played 
using 3WPlayer that is completely free

Please visit [www.3wplayer.com](www.3wplayer.com)

So, I am going to scrap this file and borrow the original DVD.  Looks like there is some messy DRM thing here..... 
Now for a fact, I know that this 3WPlayer is a malware. I will need to go back to the office and find the idiot who did this rip and then probably, I will use a sledgehammer to swing in the vacuum of his brains. I work in the IT team in my workplace and we are paid to ensure that the company network is safe...... Well, now one in my team just created a mess and I have to get it fixed. Hmmm, Windows gets affected by the installation of this stuff... Not Linux.

---

### Post by Krinn on 2007-05-25
3WPlayer is some malware which displays popup ads.  Fortunately it only infects Windows, so you're safe if you use Ubuntu.

Whatever you downloaded is useless, so just delete it.

---

### Post by Prometheus.172214 on 2007-05-25
Krinn >> I guessed that at a later stage after some RnD. Apparently the original DVD was converted into AVI using some software a co-worker found on in our software shelf in the office. Turns out, this was a disc which was used by the IT team for testing our intranet for attacks and all the stuff on it was Windows Malware (I wonder, why those idiots did not label so)......... Anyway, I watched the actual video in it's original DVD form and backed it up to another DVD.... Gues I should have done that before itself..... Was just lazy to go out and buy a DVD I suppose.

---

