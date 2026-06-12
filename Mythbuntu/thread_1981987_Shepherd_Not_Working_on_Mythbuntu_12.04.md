---
title: "Shepherd Not Working on Mythbuntu 12.04"
date: 2012-05-17
forum: Mythbuntu
---

### Post by daveshep on 2012-05-17
Gday, I'm hoping someone can help me here... I'm having problems getting Shepherd to work to grab EPG data. I had it working fine on previous versions of myth but it just won't work now.

First up it just seems to lock up when running as the cron job that gets set up with the --configure-mythtv command. once i kill that and try to run mythfilldatabase i get stuff like

XMLTV config file is: /home/shep/.mythtv/TV.xmltv
Error in 1:1: unexpected end of file

there is no TV.xmltv file in ~/.mythtv... if i try and run 

mythfilldatabase --update --file 1 ~/.shepherd/output.xmltv

as suggested to people with similar issues i get

Boolean type options do not accept values:
    --file
Received '1' but unassociated arguments have not been enabled

it seems --file needs more arguments eg

mythfilldatabase --update --file 1 --sourceid 1 --xmlfile .shepherd/output.xmltv

or something similar and everything i try gets the same error as above.

then i remembered Auric had an alternative grabber etc so i tried to check that out at [http://web.aanet.com.au/~auric](http://web.aanet.com.au/~auric) and it's not working either... the website gives me a

Unable to connect to database server

where has Aurics page gone?

any ideas?

cheers

shep

---

### Post by The Toastcutter on 2012-05-21
> **daveshep said:**
> 
it seems --file needs more arguments eg

mythfilldatabase --update --file 1 --sourceid 1 --xmlfile .shepherd/output.xmltv

or something similar and everything i try gets the same error as above.


Try this:[INDENT]    mythfilldatabase --update --file --sourceid 1 --xmlfile ~/.shepherd/output.xmltv
[/INDENT]

---

### Post by Lester_Burnham on 2012-05-22
Crontab entry
```
12 * * * * ~/.shepherd/shepherd --daily --quiet && mythfilldatabase --file --sourceid 1 --xmlfile ~/.shepherd/output.xmltv --quiet >/dev/null 2>&1
```

Testing if shepherd has data already
```
mythfilldatabase --file --sourceid 1 --xmlfile ~/.shepherd/output.xmltv
```

---

### Post by daveshep on 2012-05-25
beautiful, that did the trick. thanks guys ;)

---

