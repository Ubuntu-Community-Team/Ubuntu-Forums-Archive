---
title: "how to configure a delta 1010LT soundcard??"
date: 2007-10-26
forum: Multimedia Production
---

### Post by spamhippy on 2007-10-26
have been searching high and low for this hope someone here might be able to help- i've got the latest ubuntu studio installed- i'm trying to get a m-audio delta 1010lt soundcard up & running-(this computer also has an AC'97 built into the motherboard..that works fine-lol)  the computer reconizes the card (i click on the little speaker icon- it's there, envy24control brings up the card..etc) 2 of the output channels play out (ie i get sound from them..) none of the 8 input channels works (with me so far?-lol) though in ardour- i can get the sound meter to move if i plug something in (though i can't get it to record or hear what's plugged in..) 

here's the short of it...

if i'm understanding correctly- i need to get an .asoundrc file setup correct to make all 8 channels record, and all 10 outputs to play out- yet- i've searched high & low and can't find one & am completely lost when i read the 'how-to' on making an .asoundrc file- does anyone hear have a working .asoundrc file for this- or know how to configure this card? 

could my setting in jack be wrong?

any help would be greatly welcomed. i hear the delta cards are well maintained in linux- yet trying to find out how to do this has been really hard- lol.

thanks again--

---

### Post by spamhippy on 2007-10-26
just a quick update- i managed to record a track with the card under ardour= though i couldn't hear myself- but once i played it back i could hear it- so how do i ....

a) hear whatever i have plugged in?
b) get all my ouputs working?

thanx again..

---

### Post by spamhippy on 2007-10-26
nevermind-- i just figured it out-- lol.

go into jack control- click on 'connections' & make sure whatever line your plugged into goes to whatever out you plugged into- 

-well... um.. thanks

---

### Post by masarusan on 2008-04-01
Dude, you really gave me a good laugh.  Really, thanks!

So I was looking to make all my outputs work also (for playing surround movies for example).

I've got outputs 3.1 and 4.1 going to my stereo to output to the back speakers .. They can be tested for sound OK but don't get anything when I'm playing a movie..

I'd appreciate it if you could tell me how you did it...
Thanks in advance!:popcorn:

---

