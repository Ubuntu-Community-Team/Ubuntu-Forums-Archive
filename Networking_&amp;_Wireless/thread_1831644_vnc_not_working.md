---
title: "vnc not working"
date: 2011-08-23
forum: Networking &amp; Wireless
---

### Post by gh123man on 2011-08-23
hello everyone. 

i run a server and can only access it remotely. i use ssh and vnc. i am currently far away from it and will be for a while as i am in college. my house had a power failure and vnc no longer work. ssh works fine so i can remote in that way but when i connect with vnc it doesn't fail it just hangs forever. any ideas?

---

### Post by lmarmisa on 2011-08-23
I suppose that you are using Remote Desktop.

Connect to you remote server using the option -X (X11 forwarding enabled):

```

ssh -X remote_server

```

Then you can open the Remote Desktop Preferences menu on your remote server typing this command:

```

vino-preferences &

```

Check if the vnc configuration is correct.

If you need to access to your home's router/modem in order to check the port forwarding, you can open firefox remotely typing:

```

firefox &

```

I hope that these commands could help you.

Best regards,

Luis

---

### Post by gh123man on 2011-08-25
thank you! i wish i know as much about linux as you and everyone else but im learning :) 

how i fixed it (for though's with the same issue that find this post)

i used an ubuntu virtual machine (its all i had) and used the commands he listed (will not work in putty you need linux) and the changed the setting to off. rebooted it and turned vnc back on. fixed. 

thanks again.

---

### Post by lmarmisa on 2011-08-25
Great!!!. :D

Only a question: what specific item have you changed to off?. 

Please, Mark the thread as SOLVED (look at Thread Tools),

Best regards,

Luis

---

### Post by gh123man on 2011-08-28
i turned vnc off all together (i forget the exact name of the check box) and rebooted the server. then turned it back on and it works great.

just had another power failure. so i hope this trick will work again :)

and i will look into the thread tools thank you.

---

