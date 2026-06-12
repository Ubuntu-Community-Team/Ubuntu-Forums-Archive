---
title: "Help! empty schedule for no reason"
date: 2010-03-08
forum: Mythbuntu
---

### Post by itlarson on 2010-03-08
All my schedule info disappeared for no reason!  I need help because this means nothing will record.  The internet connection is good, and my schedules direct is payed up.  No changes were made to the system before this happened.  Can anyone help?

---

### Post by itlarson on 2010-03-09
I noticed that mythfilldatabase is giving an "internal Server Error" message.  Does anyone know what could cause that?

excerpt:

Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 500 Internal Server Error
2010-03-09 07:19:59 ERROR 500: Internal Server Error.

2010-03-09 07:19:59.125 Grab complete.  Actual data from  to  (UTC)

---

### Post by rhpot1991 on 2010-03-09
> **itlarson said:**
> I noticed that mythfilldatabase is giving an "internal Server Error" message.  Does anyone know what could cause that?

excerpt:

Reusing existing connection to webservices.schedulesdirect.tmsdatadirect.com:80.
HTTP request sent, awaiting response... 500 Internal Server Error
2010-03-09 07:19:59 ERROR 500: Internal Server Error.

2010-03-09 07:19:59.125 Grab complete.  Actual data from  to  (UTC)

Sorry to ask the obvious, but have you checked that your schedules direct account is active?

I would also try to check/repair the DB tables.  You can do this easily in mythweb under the settings button.

---

### Post by itlarson on 2010-03-09
My account was renewed in February.  I've never used mythweb,  is there a way to do the tables thing directly? Thanks for the reply.

---

### Post by itlarson on 2010-03-09
Nevermind- In machine status it says "expires February 23"-  not "expired February 23" and doesn't specify the year.  I assumed this meant I was current without thinking about it.  I wish schedules direct would renew automatically.  Also it would be nice if the frontend would pop up a warning dialog.

---

### Post by itlarson on 2010-03-09
No, it's still not working.

---

### Post by itlarson on 2010-03-09
Finally got it!  I had to re-do input connections, since I had been messing around in th backend settings.

---

