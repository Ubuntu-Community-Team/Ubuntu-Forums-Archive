---
title: "cant get mythlink.pl to work 11.10"
date: 2012-01-12
forum: Mythbuntu
---

### Post by jeremycobert on 2012-01-12
is anyone using mythlink.pl on mythbuntu 11.10 ?

I am having some trouble running this
```
mythlink.pl --link /mnt/pretty --format '%U-%T-%Y%m%d-%H%i-%eH%ei-%S'
```

i keep getting an error mythbox:~$ mythlink.pl: command not found

am i missing something ? i have the /mnt/pretty folder configured for read/write.

---

### Post by nickrout on 2012-01-12
the command is not, by default in your path. On my system it is in /usr/share/doc/mythtv-backend/contrib/user_jobs/mythlink.pl

You can either:

1. run it with the full path as in ```
/usr/share/doc/mythtv-backend/contrib/user_jobs/mythlink.pl --link /mnt/pretty --format '%U-%T-%Y%m%d-%H%i-%eH%ei-%S'
``` or

2. move it into somewhere in your path, like /usr/bin or /usr/local/bin

```
sudo mv /usr/share/doc/mythtv-backend/contrib/user_jobs/mythlink.pl /usr/bin/
```

---

