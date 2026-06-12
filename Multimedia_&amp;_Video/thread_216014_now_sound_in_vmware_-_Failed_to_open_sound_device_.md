---
title: "now sound in vmware - Failed to open sound device /dev/dsp"
date: 2006-07-14
forum: Multimedia &amp; Video
---

### Post by kpurcell on 2006-07-14
I have installed the latest version of VMWare Server on Ubuntu Dapper.  I have a Dell Inspiron 9300 notebook.  When I try to add sound to the vmware guest os, when it starts up it gives this error.

```
Failed to open sound device /dev/dsp: Device or resource busy
Failed to connect virtual device sound.

```

I've read some things but found nothing that seems to fit this situation.

---

### Post by Rhaurison Bergamin on 2006-07-19
Could you try this?:

[http://www.vmware.com/support/kb/enduser/std_adp.php?p_sid=pt1xPPWh&p_lva=&p_faqid=1611&p_created=1110838404&p_sp=cF9zcmNoPTEmcF9ncmlkc29ydD0mcF9yb3dfY250PTEmcF9zZWFyY2hfdGV4dD1hcnRzJnBfc2VhcmNoX3R5cGU9NyZwX3Byb2RfbHZsMT0zNyZwX3Byb2RfbHZsMj1_YW55fiZwX3NvcnRfYnk9ZGZsdCZwX3BhZ2U9MQ**&p_li=]("http://www.vmware.com/support/kb/enduser/std_adp.php?p_sid=pt1xPPWh&p_lva=&p_faqid=1611&p_created=1110838404&p_sp=cF9zcmNoPTEmcF9ncmlkc29ydD0mcF9yb3dfY250PTEmcF9zZWFyY2hfdGV4dD1hcnRzJnBfc2VhcmNoX3R5cGU9NyZwX3Byb2RfbHZsMT0zNyZwX3Byb2RfbHZsMj1_YW55fiZwX3NvcnRfYnk9ZGZsdCZwX3BhZ2U9MQ**&p_li=")

Let us know if this works fine.

---

### Post by mcman42 on 2006-07-28
> **Rhaurison Bergamin said:**
> Could you try this?:

[http://www.vmware.com/support/kb/enduser/std_adp.php?p_sid=pt1xPPWh&p_lva=&p_faqid=1611&p_created=1110838404&p_sp=cF9zcmNoPTEmcF9ncmlkc29ydD0mcF9yb3dfY250PTEmcF9zZWFyY2hfdGV4dD1hcnRzJnBfc2VhcmNoX3R5cGU9NyZwX3Byb2RfbHZsMT0zNyZwX3Byb2RfbHZsMj1_YW55fiZwX3NvcnRfYnk9ZGZsdCZwX3BhZ2U9MQ**&p_li=]("http://www.vmware.com/support/kb/enduser/std_adp.php?p_sid=pt1xPPWh&p_lva=&p_faqid=1611&p_created=1110838404&p_sp=cF9zcmNoPTEmcF9ncmlkc29ydD0mcF9yb3dfY250PTEmcF9zZWFyY2hfdGV4dD1hcnRzJnBfc2VhcmNoX3R5cGU9NyZwX3Byb2RfbHZsMT0zNyZwX3Byb2RfbHZsMj1_YW55fiZwX3NvcnRfYnk9ZGZsdCZwX3BhZ2U9MQ**&p_li=")



Didnt work for me

---

### Post by marsian on 2006-08-01
The following solution works for me:

run "killall esd" in a terminal
then launch vmware server

---

### Post by kpurcell on 2006-08-03
> **marsian said:**
> The following solution works for me:

run "killall esd" in a terminal
then launch vmware server

That worked but do I have to do that every time I run it?  If so, is there a way to set up a sript that I could use to killall esd and then run vmware?

---

### Post by fakie_flip on 2006-08-22
Is there a better way to shut down esd without killing it? I guess the reason for killing esd is because you cant have sound in the host and guest at the same time, but what about when you stop using vmware? Is the sound there again, or do you have to reboot to get it back?

---

