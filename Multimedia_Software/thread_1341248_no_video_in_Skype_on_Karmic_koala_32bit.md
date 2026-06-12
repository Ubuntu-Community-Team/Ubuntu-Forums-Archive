---
title: "no video in Skype on Karmic koala 32bit"
date: 2009-11-29
forum: Multimedia Software
---

### Post by mayacreator on 2009-11-29
Hi, my camera Canyon CNP-WCAM313
( 0ac8:3420 Z-Star Microelectronics Corp.) works fine with Skype in Ubuntu Jaunty , but in Ubuntu Karmic  only microphone works in Skype, when I turn video on camera indicator turns on too but no video appears, only black window. In Cheese video works fine.

---

### Post by mayacreator on 2009-11-30
I solve my problem, just edited my ~/.Skype/<username>/config.xml by adding the Video element. Mine did not have a <Video> element, I put it under <Lib> 
 ```
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

```

I found it here [http://setdosa.blogspot.com/2009/01/fixing-green-screen-for-skype-video-on.html](http://setdosa.blogspot.com/2009/01/fixing-green-screen-for-skype-video-on.html)

---

