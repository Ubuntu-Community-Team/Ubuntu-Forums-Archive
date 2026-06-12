---
title: "Sending Yahoo E-mail"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by user2037 on 2009-07-10
Freepops is a great package for receiving e-mail from Yahoo in a client application like Evolution or Thunderbird. However, it doesn't support sending. Thunderbird's Webmail can send but it is broken at the moment with send attempts producing "negative vibes".

Ypops works for receiving and sending with Wine. I'd rather not use Wine.

Are there any other free options for sending through Yahoo from an SMTP client?

---

### Post by Short__Error on 2009-07-10
This would be nice i have not found one my self but do belive there is one out there hope someone can help you and me. :lolflag:

---

### Post by mattman on 2009-07-10
I use Thunderbird with the Webmail extension. It works OK for the most part except for not remembering my password from one session to the next. If you decide to use it make sure you are using the yahoo mail beta web interface and change the setting in the Thunderbird extension to match this. The classic interface does not function at this time. Hope this helps.
[http://webmail.mozdev.org/](http://webmail.mozdev.org/)

---

### Post by donato roque on 2009-09-14
I finally made Freepops to work.  I am receiving my yahoo emails.  First download Freepops from synaptic.  Please include the Updater Gnome.  After downloading, update freepops by going to Application>Internet>Freepops Updater.  Select your account from the popup window.  Allow to update.

If you have not entered you account details in Evolution please do so.  Just go to Evolution  Edit>Preferences click on Add to add your free pop account.  This is important:  in the receiving tab in filling out username please INCLUDE the domain e.g. [email]username@yahoo.com[/email].

If you encounter an error in sending password from evolution.  You will have to edit Seahorse.  This is the password key manager in Gnome.  You will have to delete the old saved password for the account.  Go to Applications>Accessories>Password and Encryption Keys  to the Password tab.  Right click the appropriate account.

You can make Evolution get your mail by pressing the Send/Receive button or F9.  Give your email account password when prompted.  You should be prompted because we deleted it in the previous steps.

---

### Post by donato roque on 2009-09-14
I was able to send my mail using Yahoo account.
Make the Yahoo account your default in Evolution (if you have multiple accounts in Evolution).

---

