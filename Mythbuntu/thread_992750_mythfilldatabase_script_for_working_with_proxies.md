---
title: "mythfilldatabase script for working with proxies"
date: 2008-11-25
forum: Mythbuntu
---

### Post by moorsey on 2008-11-25
I have a script in cron.daily to run the mythfilldatabase with EPG data.  It will not work as default as I am behind a proxy here and for whatever reason mythbuntu doesn't support that.

So this is the script:
```
#!/bin/sh
http_proxy=http://myproxyhere:1234 tv_grab_uk_rt --output /home/martin/xmltvuk.xmltv
mythfilldatabase --file 1 /home/martin/xmltvuk.xmltv
```

but, this doesn't run for whatever reason, have I missed something?

Hopefully this script will be useful for others, I cobbled it together from others suggestions!

---

### Post by ian dobson on 2008-11-25
Hi,

Have a look here [http://osdir.com/ml/tv.xmltv.general/2003-01/msg00031.html](http://osdir.com/ml/tv.xmltv.general/2003-01/msg00031.html)

I imagine your script should look like this:-

```

#!/bin/sh
export http_proxy=http://myproxyhere:1234 
tv_grab_uk_rt --output /home/martin/xmltvuk.xmltv
mythfilldatabase --file 1 /home/martin/xmltvuk.xmltv

```

Try running the script as the mythtv user and see what it does.

Regards
Ian Dobson

---

### Post by moorsey on 2008-11-25
oops, I should have mentioned, the script runs fine if i run it in the terminal:

```
sudo \etc\cron.daily\mythbuntu-backend
```

but does not run as a cron job as it should.

Will take a look at that link, thanks!

edit:  I don't have to run it as admin, works either way

just looking into running cron jobs as a certain user now:

minute hour dom month dow user cmd

going to try that instead of putting it in cron.daily

---

### Post by ian dobson on 2008-11-25
Hi,

why not do a 

```

su - mythtv -s /Path/to/your/script

```

just test it with su - mythtv -s /usr/bin/whoami

where mythtv is the user you want to start the script as.

Regards
Ian Dobson

---

