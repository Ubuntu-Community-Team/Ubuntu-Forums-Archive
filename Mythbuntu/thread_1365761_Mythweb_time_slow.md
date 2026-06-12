---
title: "Mythweb time slow"
date: 2009-12-27
forum: Mythbuntu
---

### Post by benlyboy on 2009-12-27
Hi all 

I have been playing with mythweb the last few nights. I have notice that the time shown on the page is one hour slow. When you bring up a listing,  it too shows listings starting one our earlier. My mythbox is a combined front and back end. Both the system time and time shown in the front end are right. The time on the laptop I am using to view mythweb is also right, only myth web is an hour slow
Does any one have any idea why this would be...?

---

### Post by azmyth on 2009-12-27
You need to set the proper time zone in the php.ini file then restart apache.

For example, mine reads.

date.timezone = America/Phoenix

---

### Post by benlyboy on 2009-12-27
Hi azmyth thanks for the reply


I made the changes you recommended to the php.ini file. The time zone setting was blank so I set to match my other two computers

But it has not made any difference that I can see.

---

### Post by azmyth on 2009-12-27
Create a file called date.php

```

<?php
echo date('l jS \of F Y h:i:s A');
?>

```

Then run it via command line

php date.php

Does this match with your current system time?

---

