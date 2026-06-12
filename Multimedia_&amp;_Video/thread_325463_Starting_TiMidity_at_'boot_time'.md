---
title: "Starting TiMidity at 'boot time'"
date: 2006-12-25
forum: Multimedia &amp; Video
---

### Post by jott27 on 2006-12-25
I have rosegarden 1.4.0 working after I initiate TiMidity with
$ timidity -iA -B2,8 -Os1l -s 44100 on a terminal and start rosegarden in a second terminal.
 
I am not sure that this would be a good idea, but i am asking the question anyway:
Is there a way to start TiMidity at boot time automatically? Maybe with a script?
My sound card is a SBLive!(ver 7)

---

### Post by Rippey on 2006-12-25
I don't know if it a good idea to strart these programs on boot since I'm not formiliar with then, it is however posible to do.

what you need to do is make a script in /etc/init.d like this:

touch /etc/init.d/starttimidity (or any other name you like)

then open it with a text editor and copy the following lines to it

#!/bin/bash
timidity -iA -B2,8 -Os1l -s 44100 && <command for starting rosegarden> &

save it

make sure ownership is set to root (chown root.root /etc/init.d/starttimidity)
and make it executable (chmod 755 /etc/init.d/starttimidity)

now check what runlevel you're in with "runlevel" 
this should give you an output something like this "N 2"

go to /etc/rc#.d where # = the runlevel you're in.

now make a symlink to the file you have created earlier 
ln -s /etc/init.d/starttimidity S99starttimidity

chmod 777 S99starttimidity
chown root.root S99starttimidity

and you should be done

good luck

---

### Post by jott27 on 2006-12-26
> **Rippey said:**
>  
#!/bin/bash
timidity -iA -B2,8 -Os1l -s 44100 && <command for starting rosegarden> &

Your script works fine ! The only change I made was that I 
eliminated the last part '&& ....etc'.
This way does it not only work for rosegarden, but also for pmidi.
Thanks for the help.

---

