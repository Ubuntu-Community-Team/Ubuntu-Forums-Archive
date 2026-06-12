---
title: "Reconnecting network mounts"
date: 2007-11-24
forum: Mythbuntu
---

### Post by Trimble Epic on 2007-11-24
I want to get some kind of menu item that I can select using my remote that will cause ubuntu to re-attempt to mount network mounts.

Here's the scenario.

I have various video files on various computers around the house.. some on my computer, some on my wife's computer, and some on my NAS.  My wife likes to turn her computer off to save electricity.  When I want to watch a video that's stored on her computer, currently, I have to power up her machine, then reboot the myth so that the myth will reattach to her drives and show the videos in the Watch Videos section.

I would love to have a menu item that would cause Myth to try to remount missing drives when I tell it to.  I believe the command is "sudo mount -a" ...   but how can I create a menu item in Myth's menus to do this using the remote, and so that I don't have to enter my user's password?

Is it possible to get ubuntu to periodically attempt to reconnect these automatically?

Thanks!

---

### Post by stevetv on 2007-11-24
editing menus is quite easy.  the menu pages are contained within .xml files located in 
```

/usr/share/mythtv

```

its very easy to add buttons, something ive done for things like running external programs.  i dont know how to get around the problem associated with using sudo though.. but surely that can be done.. im just not interested enough to figure it out for you.

if you at the code of one of the menus, you see they have a really simple format, made slightly more verbose by containing many languages.

i added a button to lauch k9copy from the dvdmenu by adding this code 

```


   <button>
      <type>DVD_COPY</type>
      <text>Copy DVD</text>
      <action>EXEC /usr/bin/k9copy</action>
   </button> 


```

now, when i click on the dvd menu, an extra button called "Copy DVD" exists.  when i click that button, it performs the action EXEC /usr/bin/k9copy ..

the font etc is determined by the theme so you dont need to worry about any of that.

you'll be able to do the same thing, but you'll need to echo the user password to be able to do anything in sudo. ..

---

### Post by uopjohnson on 2007-11-25
check out 
```
man sudoers
```
You can edit what commands can be run sudo and by whom.  You could set it up so mount -a can be run my your myth user without a password.  
I would give you the exact command, but I haven't messed with this in a while.  I'm sure if you google suoders you will find something. 

The thing I do remember is that you have to edit the file using visudo and not your usual editor.

---

### Post by Trimble Epic on 2007-11-25
Thanks guys, I'll look into this when I get a chance to work on my box again.

---

