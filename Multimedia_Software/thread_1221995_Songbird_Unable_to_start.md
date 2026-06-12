---
title: "Songbird Unable to start"
date: 2009-07-24
forum: Multimedia Software
---

### Post by babin on 2009-07-24
Hi
I have a problem with songbird. I opened Songbird in terminal with Sudo, and then after I closed it, songbird doesn't work, with or without Sudo. when I open it shows me an error : [COLOR="Red"]Songbird is unable to start[/COLOR], and when I click Delete library and restart it still doesn't work and shows me this error again, and when I click on continue anyway it goes to first Setup page and then songbird starts but I can't add media to songbird and if I close and open songbird again, it shows me this error again...
by the way, In terminal it shows me this error too :  ```
Could not create the MMKeys instance
```

I don't know why it doesn't work, I just tried open Songbird whit sudo... :confused::(

I use songbird on Ubuntu 9.04 jaunty X64

---

### Post by martinbaselier on 2009-07-24
first try setting you as owner of the files:

find ~/.songbird2/ -exec sudo chown  YOURUSERNAME:YOURGROUPNAME {} \;

replace YOURUSERNAME and YOURGROUPNAME with your user and group name

If that doesn't help, try removing your songbird settings folder:
**sudo rm ~/.songbird2 -rf**

---

### Post by babin on 2009-07-25
Songbird is working again :D  I couldn't find ~/.songbird2/ -exec sudo chown but I remove /.songbird2 and then it works again

Thank you so much :)

---

