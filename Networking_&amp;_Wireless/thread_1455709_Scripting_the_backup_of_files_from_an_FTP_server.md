---
title: "Scripting the backup of files from an FTP server"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by Barry Cent on 2010-04-16
Hi,

Admins, please move this thread if there is a better suited place :confused:

I'm looking to make a script that will connect to an FTP server on my network, download a few directories to a local directory, and tar them up.

I'm having some problems with the ftp command though. I've just about managed to connect to the FTP server using the FTP command, however I'm not too sure what to do next, let alone incorporate this into a script.

Would anyone be able to give me some help on how to do this?

Thanks,

Joe

---

### Post by xifer on 2010-04-16
maybe something like this

```

#!/bin/sh
HOST='ftp.users.disorg.net'
USER='yourid'
PASSWD='yourpw'
FILE='file.txt'
LOCATION='/user1/data'
ftp -n $HOST <<END_SCRIPT
quote USER $USER
quote PASS $PASSWD
cd $LOCATION
get $FILE
quit
END_SCRIPT
exit 0


```

---

### Post by Barry Cent on 2010-07-07
Hey,

Meant to update this thread _much_ earlier, but only just got chance.

> **xifer said:**
> maybe something like this

```

#!/bin/sh
HOST='ftp.users.disorg.net'
USER='yourid'
PASSWD='yourpw'
FILE='file.txt'
LOCATION='/user1/data'
ftp -n $HOST <<END_SCRIPT
quote USER $USER
quote PASS $PASSWD
cd $LOCATION
get $FILE
quit
END_SCRIPT
exit 0


```

xifer: Thanks very much for your reply. I was getting ready to give up before you replied!

I was unable to use the script that you suggested to get ftp to do what I wanted.

Whilst messing around with your script though, I came accross the utility 'lftp', which I was able to script to do exactly what I wanted!

More information on lftp can be found [here]("http://lftp.yar.ru/").

I've basically used lftp to mirror the FTP server to a local directory, which I then tar, bzip and copy to an backup HDD.

The following line is what I use to mirror a folder on the FTP server to the pwd:

```
lftp -c mirror ftp://<username>:<pass>@<FTP_IP>/<folder>/
```

Thanks xifer for you time!

Cheers,

Joe

---

