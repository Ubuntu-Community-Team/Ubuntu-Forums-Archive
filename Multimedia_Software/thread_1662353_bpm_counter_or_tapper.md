---
title: "bpm counter or tapper"
date: 2011-01-07
forum: Multimedia Software
---

### Post by dsjstc on 2011-01-07
I'm looking for an app, applet, or plugin to manually count bpm and set the tag in currently-playing audio files.

Extra points if it works in Guayadeque, but Rhythmbox would be great too.

---

### Post by Jerommel on 2011-03-27
O yes, that would be very nice !

---

### Post by FrankT-Qc on 2011-05-31
Hi there...

I made this tiny python script. It doesn't write to files but hey it's better than a kick in the face.

Anyway, you might want to change the filter (alpha) value to suit your needs.

[LIST]
[*]alpha = 1 means no filter
[*]alpha ~= 0.1 is my favorite (I swing around 200 BPM...)
[*]alpha = <.01 takes forever
[*]alpha > 1 will give you absolute crap.
[/LIST]

```

#! /usr/bin/python3

from datetime import datetime, timedelta

alpha = 0.1

def main() :
    print("""
Drive a punch on your Enter key on every beat; BMP will be shown
Filter : {}
""".format(alpha))
    lp = None
    lastTick = None
    
    while True :
        input()
        tick = datetime.now()
        if lastTick :
            p = tick - lastTick
            p = p.days * 24*3600 + p.seconds + p.microseconds / 1000000
            if lp :
                lp  += alpha * (p - lp)
            else :
                lp = p
            bpm = 60 / lp
            print("BPM : {:5.0f}".format(bpm))
        lastTick = tick


if __name__ == "__main__" : main()

```

---

### Post by FrankT-Qc on 2011-05-31
oh yeah, but if you find something for Rhythmbox, let me know !!!

---

