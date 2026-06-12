---
title: "jkeys - joystick/gamepad/lirc controlled games on mythbox"
date: 2008-08-31
forum: Mythbuntu
---

### Post by KillerKiwi on 2008-08-31
Here's some code I've been using on so I can get more linux games working for the mythbox

It takes a simple config file and turns joystick / lirc events into x key presses

ie

```
jkeys frozen-bubble.config frozen-bubble
```

here's a config file

```

<config>
    <joystick id="0">
        <axis number="0" low="Left" high="Right" />
        <axis number="1" low="Up" high="Down" />
        
        <button number="0" key="Space" />
        <button number="1" key="Return" />
        <button number="2" key="a" />
        <button number="3" key="b" />
        <button number="4" key="c" />
        <button number="5" key="d" />
        <button number="6" key="z" />
        <button number="7" key="x" />
        <button number="9" key="Escape" />
        <button number="10" key="p" />
    </joystick>
    
    
    <remote>
        <button code="OK" key="Return" />
        <button code="Stop" key="Escape" /> 
        <button code="Pause" key="p" /> 
        
        <button code="Up" key="Up" />
        <button code="Down" key="Down" />
        <button code="Right" key="Right" />
        <button code="Left" key="Left" />      
    </remote>
    
</config>

```

Start frozen bubble with the frozen-bubble config, now you can play frozen bubble with a joypad.. yay

code is at
[https://jkeys.googlecode.com/](https://jkeys.googlecode.com/)

It works, next step is to add fake mouse events as well so the gamepad can move the mouse pointer...

*Yes I know you can set the joypad as an x input device but I want the input customised per game and easy to setup*

---

### Post by OliW on 2010-01-01
It works great. My only issue with it is when I use it with my media centre app (Boxee in my case), over time, processes fork all over the place and it ends up using all the RAM in the history of the universe.

It would be awesome-er if there was some separation between the processes, so jkeys just listened to the joypad and sent keyboard events to the system and left the actual app (ie boxee) well alone.

So then even if jkeys forkbombed itself, I could just restart jkeys without having to kill everything spawned from it.

I'd have posted this on the jkeys site but it's not up right now.

---

### Post by SpartacusRex on 2010-03-08
Hi,

I am using an AMD64 with 64GBSSD drive, mythbuntu boots in 10secs, and when I ran JKeys I was getting an error 

Exception in thread Thread-1:
Traceback (most recent call last):
  File "/usr/lib/python2.6/threading.py", line 525, in __bootstrap_inner
    self.run()
  File "/usr/lib/python2.6/threading.py", line 477, in run
    self.__target(*self.__args, **self.__kwargs)
  File "/home/spartacus/jkeys/jkeys-read-only/joystick.py", line 115, in run
    res = gethatcode(ev)
NameError: global name 'gethatcode' is not defined

I went into joystick.py and removed 

if ev.type == pygame.JOYHATMOTION:
                        res = gethatcode(ev)
                        if self.debug: print "UNHANDLED JOY HAT code: ", res

                    elif

on line 115, keeping the rest of the IF statement. 

Now it works.

Not sure why or what just thought some might have same problem.

---

### Post by adibudeen on 2010-04-05
I got the same error, and since I am not familiar with Python, can you please post exactly how the lines look in your joystick.py file?

---

