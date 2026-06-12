---
title: "Install new mythbuntu instance and import old DB"
date: 2007-11-22
forum: Mythbuntu
---

### Post by moodog on 2007-11-22
I've had a hand configured/installed mythtv running fine on Ubuntu for about 18 months now, but lately it has become a bit stuffed due to a number of reasons (the DB is fine, the general Ubuntu config has got a bit messy). I'm wondering if it would be possible to install mythbuntu on a new partition on the machine, export my DB from the old myth install and import it into the new MythBuntu install, and all should work fine? Would I also need to copy over the channel information? What else may need to be migrated? I don't want to lose all of the recording info etc.

Also, does Myth Control Centre support the Grey and silver hauppauge remote control?

---

### Post by uopjohnson on 2007-11-25
Yes.  You can move the db without a problem.  Here are the steps from the mythtv wiki:
```

mysqldump -u<myth_user> -p --extended-insert  --add-drop-table --databases mythconverg  > mythdatabase.bak
Password: <myth_password> // this can by found in /etc/mythtv/mysql.txt

```

You could then use your <myth_user> to restore the data to the database:
```

$ mysql -u<myth_user> -p < mythdatabase.bak
Password: <myth_password>

```

---

