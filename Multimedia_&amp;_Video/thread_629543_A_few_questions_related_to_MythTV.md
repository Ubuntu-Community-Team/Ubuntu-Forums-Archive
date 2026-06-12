---
title: "A few questions related to MythTV"
date: 2007-12-02
forum: Multimedia &amp; Video
---

### Post by bconverse on 2007-12-02
So I've been looking for answers to these lingering MythTV questions for a while, to no avail. I'd appreciate any links/first hand experience help anyone can offer.

1)I hate how MythTV has to pre-scale the theme at start up..is there any way to set this so that it does not have to do it every time at startup?  I

2) I want to make the green power button on my happauge remote to start/stop mythTV.  I've found some guides on this subject, but they seem rather confusing to me.

3) Whenever I watch TV, the aspect ratio resets ittself.  I have a widescreen monitor, and I find the "widescreen zoom" setting works best for me, but every time I turn on the TV it is back to 4:3 and I have to change that ratio every time.  Any way to make this a permanent change?

4) There is a similar problem when watching videos in my media library.  I've tried messing with Mplayer, changing the aspect ratio, but it doesn't change anything at all when being used in conjucntion with MythTV.


That about covers it...Thanks for anything you can offer..

---

### Post by bconverse on 2007-12-03
bump

---

### Post by Scorpuk on 2007-12-04
1. Not sure

2. I think the following may help you:

Start a terminal and type the following:

```
screen -S remote
```
This will create a seperate terminal for the program you are going to run next

```
irexec
```

After this program starts press the following keys:

CTRL+A
CTRL+D

This will detatch the screen and leave it running in the background

You can always see what screens are runnign by using the following command:

```
screen -ls
```   
Thats a lowercase L btw ;)


You can now add the following to your lircrc file:

```

begin
    prog = irexec
    button = [name of power button - dependant on your remote]
    config = mythfrontend
end

begin
    prog = mythtv
    button = [name of power button - dependant on your remote]
    config = Esc 
end

```

Sadly I cannot find an option to quit mythfrontend other than pressing escape until you get the option to exit and then hit OK to accept :(

If you dont know the name of the green power button on your remote then run the following program and press it a few times:

```
irw
```

This should then give you the name associated with that button.


The above will prrobably work, not at home to try it out, as lirc will apply whichever program has focus. IE if mythfrontend is running and has focus, ie you cant see any other window on your screen, then lirc will apply the option for mythtv when you press the power button. If mythfrontend isnt running and irxec is running in a screen in the background then mythfrontend shoudl start. Either way it won;t cause any problems with your system if it doesnt work.

Basically you can use irexec to let your remote control start applications:

```

begin
    prog = irexec
    button = [button]
    config = [program]
end

```


3. From Mythfrontend:

```
Utilities/Setup -> Setup -> TV Settings -> Playback
```

The option you want is "Aspect Override: " and select the aspect ratio you want.

4. Not sure you can...

---

### Post by bconverse on 2007-12-04
Great! Thanks for your help!

---

### Post by bconverse on 2007-12-05
> **Scorpuk said:**
> 1. Not sure

2. I think the following may help you:

Start a terminal and type the following:

```
screen -S remote
```
This will create a seperate terminal for the program you are going to run next

```
irexec
```

After this program starts press the following keys:

CTRL+A
CTRL+D

This will detatch the screen and leave it running in the background

You can always see what screens are runnign by using the following command:

```
screen -ls
```   
Thats a lowercase L btw ;)


You can now add the following to your lircrc file:

```

begin
    prog = irexec
    button = [name of power button - dependant on your remote]
    config = mythfrontend
end

begin
    prog = mythtv
    button = [name of power button - dependant on your remote]
    config = Esc 
end

```

Sadly I cannot find an option to quit mythfrontend other than pressing escape until you get the option to exit and then hit OK to accept :(

If you dont know the name of the green power button on your remote then run the following program and press it a few times:

```
irw
```

This should then give you the name associated with that button.


The above will prrobably work, not at home to try it out, as lirc will apply whichever program has focus. IE if mythfrontend is running and has focus, ie you cant see any other window on your screen, then lirc will apply the option for mythtv when you press the power button. If mythfrontend isnt running and irxec is running in a screen in the background then mythfrontend shoudl start. Either way it won;t cause any problems with your system if it doesnt work.

Basically you can use irexec to let your remote control start applications:

```

begin
    prog = irexec
    button = [button]
    config = [program]
end

```


3. From Mythfrontend:

```
Utilities/Setup -> Setup -> TV Settings -> Playback
```

The option you want is "Aspect Override: " and select the aspect ratio you want.

4. Not sure you can...


Actually, on second thought.  I am having some trouble locating my the correct LIRC file to edit. Otherwise, I got it set up to that point.

---

### Post by bconverse on 2007-12-05
Also, since you seem to know have looked into the remote settings moreso than I have, do you happen to know why only some of the buttons work on the Happaugue 45 button remote? I used the Mythbuntu control center to set up my LIRC initially, I don't know if that has anything to do with it. But, I only the really basic buttons work...for example, if I want to go "back" in the menus, I have to use the stop button instead of the back button that is also on the remote.  The main menu button doesn't do anything either, among numerous others.

---

