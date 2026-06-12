---
title: "Upstart issues,.. don't understand....."
date: 2014-03-25
forum: Mythbuntu
---

### Post by diyhouse on 2014-03-25
I am running ubuntu 12.04 with myth 0.27...
Things are all working well except I cannot get mythbackend to start correctly from it designed upstart job.

I have been trying to follow:- [http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration](http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration)
but this just leaves me a little confused.

I have created /etc/init/mythtv-backend.conf,.. no problems with this bit....


but he next step to "create a symlink referencing the upstart-job binary in /etc/init.d or /etc/rc.d/init.d"
confuses the heck out of me...


to me this says,.. ln -s /etc/init/mythtv-backend.conf /etc/rc.d/init.d/mythtv-backend.conf


and there are no "binary files" referenced here,.. they are all script files.... ( sorry if I have the wrong end of the stick ) and the file upstart-job already exists,.. do I overwrite it,.. I get nervous when overwriting system files....


Can someone explain to me what are the exact commands I need to enter


And then the why do "ln -s /lib/init/upstart-job /etc/init.d/mythtv-backend",.. the text does not explain why,..
I am now really confused with these instructions,.. as I may just be reading too much between the lines.

And this link already exists,... and there's a load more other files also linked to /lib/init/upstart-job

How can this be?? "a many -> one link",.. my brain is going into over load...

Can someone pls explain....

---

### Post by diyhouse on 2014-06-19
The penny dropped!!,.. and figured this out eventually,..

By passing all these commands in sequence and using $0 on the command line,. the file-name itself is used as a passed parameter,.. 

obvious,.. eventually.

Regards

---

