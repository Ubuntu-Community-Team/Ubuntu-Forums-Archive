---
title: "LockScreen.app??"
date: 2008-01-14
forum: Mac OSX
---

### Post by Sweet Mercury on 2008-01-14
I'm in a pretty bad way with my MacBook, I seem to have "bricked" it. This is a repost of something I posted on an apple specific board and haven't heard a response back yet:

I apologize in advance if this question has been asked (a search for lockscreen.app gave me nothing), or if this is the wrong forum area. (I'm sure a moderator can move it.)

The problem I'm having is this: I wanted to assign the "squeeze" option on my Mighty Mouse to trigger my screen saver (thus locking my screen, since I have to enter my password to get back). I assumed that the screen saver was a .app, the way expose, the dock, and spaces are. So in searching through the Utilities, I found something called LockScreen.app and tried that out, which was apparently a huge mistake.

What happened was my screen showed me a full sized picture of a closed padlock, and the computer became unresponsive. I was unable to come up with any key combination to break out of it, or to use cmd+opt+esc to break out.

I decided the only thing I could do was to shut down the MacBook. Now, however, it will not boot back up. I power it up, it shows me the "Leopard" background and the dialog box to enter my admin password (which I have it set to do on boot-up), and then the dialog box disappears leaving me with a locked screen after I enter the password. I don't know what to do, and I do not want to reinstall Leopard and lose all my data. I'm still in the middle of switching over from my PC, and I am not sure what info I have backed up where yet. I could potentially lose some important stuff.

Any suggestions would be helpful, at this point. Why is there a program that does this? What purpose does it serve? 

I did Google it. All I got were forum/blog posts that told me not to run the program, and several forum threads about how to change the padlock image.)

Edit again: This seems to be the location of the app: /System/Library/CoreServices/RemoteManagement/ AppleVNCServer.bundle/Contents/Support/LockScreen.app

---

### Post by handy on 2008-01-14
If all else fails call Apple's help desk?

I believe that they will have all the answers you need.

If your machine is less than 90 days old it is free call too.

---

### Post by Sweet Mercury on 2008-01-14
> **handy said:**
> If all else fails call Apple's help desk?

I believe that they will have all the answers you need.

If your machine is less than 90 days old it is free call too.

I got in touch with a guy who's proficient in the Unix command line. We've been trying a few things.

Unfortunately, the MacBook is old. First Gen.

---

### Post by handy on 2008-01-14
> **Sweet Mercury said:**
> I got in touch with a guy who's proficient in the Unix command line. We've been trying a few things.

Unfortunately, the MacBook is old. First Gen.

They should still have the info' I would think?

As I say if comes down to it, & if they can't give you the info' then they really have no right to charge you.

---

### Post by foehammer on 2008-05-08
I kno this is a bit late but the LockScreen.app is an app thats used by the program Apple Remote Desktop to lock remote screens.

I use Deskshade with AppleScripts. 

```

tell app "Deskshade"
lock
end tell
```

and 

```

tell app "Deskshade"
unlock
end tell
```

Does the job provided u allow Deskshade to use scripts in its preference options.

---

### Post by mattconz on 2008-12-09
Try this:

as your computer boots up, but before the grey apple logo, hold apple + s. this boots up your computer in single user mode. then go to /System/Library/Startup Items and delete the app if it is there. alternateively, you can delete the app itself. 

Also, you could use dsenableroot and login as root. I don't know if this will work, though.

---

### Post by NoSmokingBandit on 2008-12-09
Safe mode will do it, but i wouldnt go about deleting the app. first just try removing the binding from the mighty mouse then check your login programs and remove it if its there. If all else fails i would rename the app, but dont delete it in case you find that its important for something.

---

### Post by 3rdalbum on 2008-12-12
Mega bump... I think he's probably reinstalled OS X by now. The LockScreen.app is still applied after restarts too.

---

