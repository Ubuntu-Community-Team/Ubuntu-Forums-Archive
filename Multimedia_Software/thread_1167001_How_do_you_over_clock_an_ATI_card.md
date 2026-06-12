---
title: "How do you over clock an ATI card?"
date: 2009-05-22
forum: Multimedia Software
---

### Post by Gothamite on 2009-05-22
How do you over clock an ATI card?

I have ubuntu 8.04 and an HD 2400 pro.

Thanks.

---

### Post by raymondh on 2009-05-22
> **Gothamite said:**
> How do you over clock an ATI card?

I have ubuntu 8.04 and an HD 2400 pro.

Thanks.

[http://forums.legitreviews.com/about8827.html](http://forums.legitreviews.com/about8827.html)

Remember that it is so much easier to "fry" your card than to overclock it.  Be careful.

Make sure you have temp-controls in place (i.e. a good heatsink, a working, continuous fan, etc)

Regards,

---

### Post by Gothamite on 2009-05-22
Hey thanks.
By the way I do have a large heatsink and continuous fan and I have heard that I can over clock this card to double the megahertz safely so I should be good.

---

### Post by markharding557 on 2009-05-22
[http://forums.legitreviews.com/about8827.html](http://forums.legitreviews.com/about8827.html)
this link is aimed at windows users using windows software i think the op needs something more linux based.

---

### Post by Melcar on 2009-05-22
Provided you have a properly installed fglrx driver, you first need to enable Overdrive:

```
aticonfig --od-enable
```


The command aticonfig will give you a long list of parameters you can use.  These are the ones that have to do with Overdrive:

```
7. ATI Overdrive (TM).
       List adapters          :  aticonfig --list-adapters
       Get Clocks of 0        :  aticonfig --adapter=0 --od-getclocks
       Set new Clocks for 0   :  aticonfig --adapter=0 --od-setclocks=770,1126
       Test out 3D            :  atiode -P60 -H localhost:0; echo $?
       Check Temperature of 0 :  aticonfig --adapter=0 --od-gettemperature
       Commit changes for 0   :  aticonfig --adapter=0 --od-commitclocks

     ***note***
             atiode is a stress application you start with a required
             parameter -P which specifies the test duration and the optional
             -H parameter to target a specific display to use.  For example
             atiode -P 600 -H localhost:0 would test display 0 for 10 minutes
             the return code from the application is the test result
             0: Test successfully completed.
             1: Invalid command-line parameters.
             2: Test failed because of rendering errors.
             3: Target adapter not found.
             4: Test aborted due to unknown reason
```

---

### Post by Gothamite on 2009-05-25
Thank you for your reply, but whenever I to enter an ATI overdrive command into the terminal it gives me this error:
 
"ERROR - ATI Overdrive(TM) is not supported on Adapter 0 - ATI Radeon HD 2400".
 
If this is fixable it would be great if you would post here on how to do it.
Thanks.

---

### Post by jordan4ibanez on 2011-02-28
bump!!!

the proprietary driver sucks doesn't allow OCing lol

you have to go to ati's website and get pci drivers...but make sure you unninstall the other one lol:lolflag:

---

