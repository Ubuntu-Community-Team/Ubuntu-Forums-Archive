---
title: "Linking channels to listings"
date: 2010-01-12
forum: Mythbuntu
---

### Post by jammln on 2010-01-12
Hi All,

Still very new to this so apologies for the newb questions.

I've got 9.01 installed and having had some fun with my novat-500 and lirc I have now got to a sticking point that I haven't found any help for.

I have set up my Source as Radio Times XMLTV which pulls listings in fine, and I have decided to use a manual loading of channels.conf (because of some issues with tuning). Both of these work fine. 

The problem is that the program guide appears empty and whilst watching tv there are no listings.

Having a quick dig in the database shows me this:

```
mysql> select count(*), ch.chanid, ch.name from channel ch left join program pg on pg.chanid=ch.chanid group by ch.chanid;
+----------+--------+-----------------------------------+
| count(*) | chanid | name                              |
+----------+--------+-----------------------------------+
|        1 |   1001 | BBC ONE                           |
|        1 |   1002 | BBC TWO                           |
|        1 |   1003 | ITV1                              |
|        1 |   1004 | Channel 4                         |
|        1 |   1005 | FIVE                              |
|        1 |   1006 | ITV2                              |
|        1 |   1007 | BBC THREE                         |
|        1 |   1009 | BBC FOUR                          |
|        1 |   1010 | ITV3                              |
|        1 |   1011 | SKY THREE                         |
|        1 |   1012 | Yesterday                         |
|        1 |   1013 | Channel 4+1                       |
|        1 |   1014 | More 4                            |
|        1 |   1015 | Film4                             |
|        1 |   1016 | QVC                               |
|        1 |   1018 | 4Music                            |
|        1 |   1019 | Dave                              |
|        1 |   1020 | Virgin1                           |
|        1 |   1021 | VIVA                              |
|        1 |   1022 | Ideal World                       |
|        1 |   1023 | bid tv                            |
|        1 |   1024 | ITV4                              |
|        1 |   1025 | Dave ja vu                        |
|        1 |   1026 | Home                              |
|        1 |   1028 | E4                                |
|        1 |   1029 | E4+1                              |
|        1 |   1030 | FIVER                             |
|        1 |   1031 | FIVE USA                          |
|        1 |   1032 | Big Deal                          |
|        1 |   1033 | ITV                               |
|        1 |   1035 | Virgin1+1                         |
|        1 |   1036 | Create & Craft                    |
|        1 |   1037 | price-drop tv                     |
|        1 |   1038 | QUEST                             |
|        1 |   1039 | SuperCasino                       |
|        1 |   1040 | Rocks & Co                        |
|        1 |   1045 | Lottery Xtra                      |
|        1 |   1070 | CBBC Channel                      |
|        1 |   1071 | CBeebies                          |
|        1 |   1072 | CITV                              |
|        1 |   1080 | BBC NEWS                          |
|        1 |   1081 | BBC Parliament                    |
|        1 |   1082 | Sky News                          |
|        1 |   1083 | Sky Spts News                     |
|        1 |   1084 | CNN                               |
|        1 |   1085 | Russia Today                      |
|        1 |   1087 | Community                         |
|        1 |   1088 | Teachers TV                       |
|        1 |   1089 | News                              |
|        1 |   1093 | Television X                      |
|        1 |   1094 | smile TV2                         |
|        1 |   1095 | smile TV3                         |
|        1 |   1096 | Babestation                       |
|        1 |   1097 | PARTYLAND                         |
|        1 |   1098 | TMTV                              |
|        1 |   1099 | Babestation2                      |
|        1 |   1105 | BBC Red Button                    |
|        1 |   1301 | 301                               |
|        1 |   1303 | 303                               |
|        1 |   1307 | TOPUP Anytime1                    |
|        1 |   1308 | TOPUP Anytime2                    |
|        1 |   1309 | TOPUP Anytime3                    |
|        1 |   1310 | TOPUP Anytime4                    |
|        1 |   1700 | BBC Radio 1                       |
|        1 |   1701 | BBC 1Xtra                         |
|        1 |   1702 | BBC Radio 2                       |
|        1 |   1703 | BBC Radio 3                       |
|        1 |   1704 | BBC Radio 4                       |
|        1 |   1705 | BBC R5L                           |
|        1 |   1706 | BBC R5SX                          |
|        1 |   1707 | BBC 6 Music                       |
|        1 |   1708 | BBC Radio 7                       |
|        1 |   1709 | BBC Asian Net.                    |
|        1 |   1710 | BBC World Sv.                     |
|        1 |   1711 | The Hits Radio                    |
|        1 |   1712 | Smash Hits!                       |
|        1 |   1713 | Kiss                              |
|        1 |   1714 | heat                              |
|        1 |   1715 | Magic                             |
|        1 |   1716 | Q                                 |
|        1 |   1718 | SMOOTH RADIO                      |
|        1 |   1722 | Kerrang!                          |
|        1 |   1723 | talkSPORT                         |
|        1 |   1725 | Premier Radio                     |
|        1 |   1727 | Absolute Radio                    |
|        1 |   1728 | Heart                             |
|      225 |   1729 | 4Music                            |
|      146 |   1730 | BBC Four                          |
|      464 |   1731 | BBC News Channel                  |
|      449 |   1732 | BBC One South East                |
|      239 |   1733 | BBC Parliament                    |
|       62 |   1734 | BBC Sport Interactive             |
|      183 |   1735 | BBC Three                         |
|      496 |   1736 | BBC Two South East                |
|      394 |   1737 | Bid TV                            |
|      488 |   1738 | CBBC                              |
|      669 |   1739 | CBeebies                          |
|      413 |   1740 | Channel 4                         |
|      413 |   1741 | Channel 4 +1                      |
|      602 |   1742 | CITV                              |
|      108 |   1743 | CNN                               |
|      104 |   1744 | Community Channel (Freeview)      |
|      389 |   1745 | Dave                              |
|      389 |   1746 | Dave ja vu                        |
|      343 |   1747 | E4                                |
|      343 |   1748 | E4 +1                             |
|      138 |   1749 | Film4                             |
|      559 |   1750 | five                              |
|      171 |   1751 | Five USA                          |
|      340 |   1752 | Fiver                             |
|      330 |   1753 | Ideal World                       |
|      364 |   1754 | ITV1 Meridian                     |
|      375 |   1755 | ITV2                              |
|      375 |   1756 | ITV2 +1                           |
|      295 |   1757 | ITV3                              |
|      420 |   1758 | ITV4                              |
|      295 |   1759 | more4                             |
|      239 |   1760 | Quest                             |
|      296 |   1761 | QVC                               |
|      636 |   1762 | Sky News                          |
|      123 |   1763 | Sky Sports News                   |
|      482 |   1764 | Sky3                              |
|       48 |   1765 | Teachers' TV (Freeview)           |
|      266 |   1766 | Virgin 1 (Freeview, Not Wales)    |
|      113 |   1767 | Virgin 1 +1 (Freeview, Not Wales) |
|      286 |   1768 | VIVA                              |
|      191 |   1769 | Yesterday (Freeview)              |
+----------+--------+-----------------------------------+
127 rows in set (0.02 sec)
```

So my guess is that I have two sets of channels now, one from the scan and one from the listings. 

I'm guessing that this is a common problem so was wondering if anyone could help?

Thanks in advance.

---

### Post by singedwings on 2010-01-28
Did you manage to solve this as I have the same problem?

---

### Post by laffinet on 2010-01-28
Go to your backend setup, channel editor, select a channel, bring up the detailed info screen for that channel. There's a "grabber" entry (forgot the exact name). What's in there ?

---

### Post by singedwings on 2010-01-29
Do you mean the xmltv id: entry? If so I did try that but I got the listings but then could not tune to that channel anymore.

---

### Post by laffinet on 2010-01-31
> **singedwings said:**
> Do you mean the xmltv id: entry? 

Yes

> **singedwings said:**
> If so I did try that but I got the listings but then could not tune to that channel anymore.

That is weird. Can you post a screenshot ?

---

### Post by singedwings on 2010-03-05
Are you still interested in this problem? I have now got to grips with the channel tuning in 9.10 and can probably help now if you need it?

Set EIT for the source so that it uses over the air guide data. Use the channel scanner in myth, I know it crashes but stick with it as it will work eventually. If you import a channels.conf you get the channels but for some reason no guide data.

I have a dvb-s card, so I had to manually add a transport and then get the channel scanner to scan for new transports while looking for channels (don't know if this applies to you?), but for some reason after the scan the guide worked apart from channels on the original transport that I had added to get the scan going. I deleted the transport that I had added and did the scan again and bingo.

I get about a week of guide data using EIT.:p

---

