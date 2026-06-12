---
title: "Skype Script"
date: 2013-01-21
forum: Multimedia Software
---

### Post by Robbyx on 2013-01-21
I would like to change the following script so that it only sends an email if a particular skype  contact has logged in. How is it done?

*(File name: skype_logged_in.sh) *
#!/bin/bash
ssmtp [email]a.com[/email] < ./skype_notifications/skype_logged_in.txt *(this contains email content)*

The above is called from the script line in the generic "Contact came Online" notification in skype. I have put the following into the skype script box:

sh skype_logged_in.sh 

Robin

---

### Post by Robbyx on 2013-01-22
Does any know an answer?

---

