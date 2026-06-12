---
title: "source ID of your card"
date: 2011-01-03
forum: Mythbuntu
---

### Post by sami8519 on 2011-01-03
Hello,

I am trying to follow this short tutorial to parse an external xmltv guide into mythtv, but I am stuck at the second step which I need to identify the source ID of my card. I am using a dual tuner DVB card so I guess there two "IDs". The command looks weird. Could anybody please translate this command for me in simpler words.
```
$ mysql -u root mythconverg
mysql> select * from cardinput\G
cardinputid
cardid
sourceid=4
etc.

```Here is the link:
```
http://www.mythtv.org/wiki/Mythfilldatabase#2._Find_out_the_source_id_of_your_card
```

Regards
Sami

---

### Post by newlinux on 2011-01-03
> **sami8519 said:**
> Hello,

I am trying to follow this short tutorial to parse an external xmltv guide into mythtv, but I am stuck at the second step which I need to identify the source ID of my card. I am using a dual tuner DVB card so I guess there two "IDs". The command looks weird. Could anybody please translate this command for me in simpler words.
```
$ mysql -u root mythconverg
mysql> select * from cardinput\G
cardinputid
cardid
sourceid=4
etc.

```Here is the link:
```
http://www.mythtv.org/wiki/Mythfilldatabase#2._Find_out_the_source_id_of_your_card
```

Regards
Sami

You tuner should only have one sourceid. Sourceid is the id to the guide source it is using. What it may have two or more of is the cardid or cardinputid if you are using multi-record. You can find the cardid and cardinputid on the mythweb backend status page without looking at the DB.

The command above connects to the mysql mythtv database (called mythconverg) and then runs a simple SQL select statement to print out the contents of the cardinput table.

```

 mysql -u root mythconverg

```
connects you to the mythconverg DB (if you have a password on the root MYSQL account you will want to do):

```
mysql -u root -pPASSWORD mythconverg
```

No space between -p and PASSWORD.
Then the next statement will be at the mysql command prompt and is a SQL select statement to print out nicely the cardinput table. This could all be accomplished in one command instead of connecting to mysql and then doing a select statement:

```
mysql -u root -pPASSWORD mythconverg -e "select * from cardinput\G"
```

If for some reason you don't know your root MYSQL password (if you have set one) you can use your mythtv user (replace root above with mythtv) and PASSWORD above with the mythtv user password (which you can get from ~/.mythtv/mysql.txt)

---

### Post by sami8519 on 2011-01-03
I cant thank you enough mate for the great explanation. I have all the information now. Thanks again.

Best Regards
Sami

---

