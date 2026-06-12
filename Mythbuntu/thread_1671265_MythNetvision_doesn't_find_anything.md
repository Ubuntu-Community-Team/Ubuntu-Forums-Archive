---
title: "MythNetvision doesn't find anything"
date: 2011-01-19
forum: Mythbuntu
---

### Post by gfojtasek on 2011-01-19
MythNetvision stopped finding anything when I upgraded to 0.24.; I just get a blank manage site subscriptions window. All of the scripts seem properly installed from what I can tell. 

I am aware from the myth wiki that this is usually caused by unmet dependencies, but I believe I have the proper version of everything on the list -- mythbrowser, flash, python bindings, python-mysqldb, python-pycurl, python 2.6.6, python-lxml. The wiki suggests running the scripts from the command line to see what might be missing, but I don't see a problem there either. for example:

```
geoffrey@mythbuntu:/usr/share/mythtv/internetcontent$ ./comedycentral.py -v
<grabber>
  <name>Comedy Central</name>
  <author>R.D. Vaughan</author>
  <thumbnail>comedycentral.png</thumbnail>
  <command>comedycentral.py</command>
  <type>video</type>
  <description>Videos of your favorite shows, whenever you want them!</description>
  <version>v0.10</version>
  <tree>true</tree>
</grabber>

```I've searched this forum and elsewhere and haven't found anything that worked. What else should I try?

---

### Post by louix on 2011-09-09
I've kinda the same problem. Check [https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/814105](https://bugs.launchpad.net/ubuntu/+source/mythtv/+bug/814105)

---

