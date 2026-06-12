---
title: "Can't log into Mythweb after recent update"
date: 2008-04-24
forum: Mythbuntu
---

### Post by pdragon04 on 2008-04-24
Ran an update last night, which included a lot of plugin                  updates, and now mythweb won't work anymore. Getting the error 

```
"Database Access Denied 

You are most likely receiving this message because you have failed to configure mythweb's database login info. 

Please see INSTALL for instructions."
```

Tried re-running the mythweb configuration to re-enter my username/password and resetting it in MCC but it still gives the same error.

Any ideas?

---

### Post by laga on 2008-04-24
Try searching the forums. I think we've had that before.

---

### Post by GordonEndersby on 2008-04-24
Same here.
Just installed 8.4 and ran an update.
I cant get in to mythweb. Im getting the same message.
I also tried re setting the mythweb password.


Gordon

---

### Post by pdragon04 on 2008-04-24
> **laga said:**
> Try searching the forums. I think we've had that before.

I have and the answer that I found was to re-run the setup (sudo dpkg-reconfigure mythweb). I've done that and tried resetting the password in MCC and still getting this.

---

### Post by pdragon04 on 2008-04-24
Well, figured out what was wrong, but not why it happened.

Look in /etc/mythtv/mysql.txt and note the password
Look in /etc/apache2/sites-available/mythweb.conf and note the password

Mine didn't match. I put the password from mysql.txt into mythweb.conf then reloaded apache and things worked again. Not sure how mythweb.conf got overwritten with a different database password.

Thanks to Laga for helping out on IRC

---

### Post by pdragon04 on 2008-04-24
Bug reported as requested by Laga -

[https://bugs.launchpad.net/mythbuntu/+bug/221532](https://bugs.launchpad.net/mythbuntu/+bug/221532)

---

### Post by GordonEndersby on 2008-04-25
Thanks, Mines sorted as well now.
It was the password mismatch.

Gordon

---

