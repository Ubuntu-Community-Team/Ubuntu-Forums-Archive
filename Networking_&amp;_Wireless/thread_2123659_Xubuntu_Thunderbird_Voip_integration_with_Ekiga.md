---
title: "Xubuntu Thunderbird Voip integration with Ekiga"
date: 2013-03-08
forum: Networking &amp; Wireless
---

### Post by djopino on 2013-03-08
Hello everyone,

I'm doing this little post because I had really hard time doing this.

So here's what I wanted to do : 

I wanted to make to have the phone numbers in my Thunderbird Contacts to be cliclable and start automatically Ekiga to call over a Voip provider. I used DiamondCard SIP provider, which is the recommendation of Ekiga folks.

Here's what you have to do:

[LIST=1]
[*]Go grab [TBDialOut]("https://addons.mozilla.org/en-us/thunderbird/addon/tbdialout/") extension for thunderbird and install it
[*]Install Ekiga and configure your Voip PC-to-Phone account. Make sure it is default.
[*]In your contacts, make sure to have the right format for the phone numbers. Don't put any "-" or spaces. You normally need to add the country prefix (1 for US and Canada). So a phone number in Canada would look like : 18197895632 (country code, area code, phone number)
[*]After that, you need to ensure that SIP url are handled throught xdg-open : 
[*]Open your /home/{user}/.local/share/applications/mimeapps.list file
[*]Add this line ```
x-scheme-handler/sip=ekiga-call.desktop
```
[*]Open Thunar or PCManFM in root mode
[*]Go to /usr/share/applications
[*]Copy ekiga.desktop in the same folder and rename it ekiga-call.desktop
[*]Again, in root mode, open the ekiga-call.desktop file
[*]Add that line at the end of the file ```
MimeType=x-scheme-handler/sip
```
[*]Go to the Exec line and replace it with ```
Exec=ekiga -c %U
```
[*]Last, you must configure TBDialOut Extension :
[*]Go to the preferences dialog of the extension
[*]Choose custom URL
[*]Enter the following (changing it if you have another provider than diamondcard) ```
sip:%NUM%@sip.diamondcard.us
```
[/LIST]

You are good to go!

For reference here are my sources of Info:
[http://superuser.com/questions/162092/how-can-i-register-a-custom-protocol-with-xdg]("http://superuser.com/questions/162092/how-can-i-register-a-custom-protocol-with-xdg")
[http://www.oak-wood.co.uk/faq/content/5/14/en/how-do-i-register-a-url-handler-for-the-sip-protocol-in-gnome-_-ubuntu.html]("http://www.oak-wood.co.uk/faq/content/5/14/en/how-do-i-register-a-url-handler-for-the-sip-protocol-in-gnome-_-ubuntu.html")
[http://www.oak-wood.co.uk/faq/content/3/19/en/how-do-i-use-tbdialout-with-ekiga.html]("http://www.oak-wood.co.uk/faq/content/3/19/en/how-do-i-use-tbdialout-with-ekiga.html")
[https://www.oak-wood.co.uk/faq/content/4/17/en/i_m-using-ekiga-for-sip-connections-but-when-i-dial-i-get-the-error-ekiga-is-already-running.html]("https://www.oak-wood.co.uk/faq/content/4/17/en/i_m-using-ekiga-for-sip-connections-but-when-i-dial-i-get-the-error-ekiga-is-already-running.html")

Jonathan

---

