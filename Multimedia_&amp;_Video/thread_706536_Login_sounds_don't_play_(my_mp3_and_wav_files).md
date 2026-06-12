---
title: "Login sounds don't play (my mp3 and wav files)"
date: 2008-02-24
forum: Multimedia &amp; Video
---

### Post by konungursvia on 2008-02-24
I copied some mp3 and wav files to the login sounds directory and selected logon and logoff sounds I like, but they don't actually play. Any ideas?

---

### Post by konungursvia on 2008-02-24
I forgot to mention: the distro supplied sound files work when selected, just the ones I add don't play.

---

### Post by polmir on 2008-02-24
Try it:
[Google]("http://www.google.pl/search?q=mp3+wav+how+to+site:ubuntuforums.org&hl=pl&lr=&start=20&sa=N")
[http://ubuntuforums.org/showthread.php?t=164614]("http://ubuntuforums.org/showthread.php?t=164614")
[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by konungursvia on 2008-02-24
Thanks polmir, but I am using all the restricted formats, and created a wav out of an mp3 I ripped from a CD I love, and am trying to use that wav as a login sound. I can play it from a  user directory using vlc, amarok, xmms, anything. But when I copy it to the root directory in which the system sounds reside, and select it as my login sound, well, it never plays when I log in. Just wondering what I was doing wrong. You misunderstood my question.

---

### Post by polmir on 2008-02-25
You don't work in root directory.  Root directory only for administrator.

---

### Post by konungursvia on 2008-02-25
Well, I didn't mean THE root directory, just the directory, owned by root, in which all the login sounds reside.

---

### Post by konungursvia on 2008-02-26
i.e., Is there a specific type of wav it has to be?

---

### Post by legolas on 2008-02-26
Bump that!  It is kind of weird- isn't .wav microsoft?  Why would a linux distribution limit its sounds to be only wav???  When I try to use an mp3 file, it says my mp3 "is not a valid wav file".

---

### Post by konungursvia on 2008-02-27
You are probably thinking of wmv, but it is strange that not all wav files will play at login, even when they will play under any media on any other occasion. Edit: No I guess you're right, MS did develop the wav as well. But I still can't get my own custom login sounds to work, does anyone know how?

---

### Post by legolas on 2008-02-28
You mean, you went System -> Preferences-> Sound-> Sounds, then selected a sound file that was a wav, and it doesn't play?
I used Audacity and exported the mp3 sounds to wav...pain in the **** if you ask me.  I wonder why they only let you use one kind of file- especially a Mirostuffed file!

---

### Post by konungursvia on 2008-02-28
Yes, that's exactly what I mean. But the sounds don't play. Doesn't even sample play from there. And I used audacity too! but no dice.

---

### Post by legolas on 2008-03-01
It is probably a permissions problem.  Heres what I do.  Don't worry about putting the files in the  same directory as the system files.  In my home folder, I have a folder called themes, and in there I put all the theme related stuff I use, themes, startup login designs, icon sets sounds etc.  That way when I reinstall, I can have my system back to the way it was in no time.  Doing this, you are the user that you should be for those system sounds to work.
If you don't want to do that, check the permissions of the files because as you copied them into the root tree, they probably turned into a root owned file so you can't access them.

---

### Post by konungursvia on 2008-03-02
Yep, but the problem persists. I have created my own wav and mp3 files which play fine in vlc and other media players. From the Sounds control panel they won't play though. And they don't play during login or logout. When I select one of the installed sounds, they do play in the sounds control panel, and during login and logout. Is there something else I need to know?

---

### Post by legolas on 2008-03-02
what software did you use to convert your sound files into wav?

---

### Post by konungursvia on 2008-03-02
Audacity I think, or maybe I used Adobe Audition while in Windows, I forget. But it plays fine in regular media.

---

### Post by legolas on 2008-03-03
Man, you got me.  You tried putting the files in your home folder right?  All I can suggest is to try to convert them agian.  Hmmm.

---

### Post by konungursvia on 2008-03-03
Actually they're in a subdirectory of the /home folder, in /home/peter/Desktop/Archives. Would that matter? BTW, thanks for the help...

---

### Post by legolas on 2008-03-03
No, it shouldn't matter- that should be ok. Did you check the permissions? If the peter user is trying to play the files, than peter should have at least read and possibly execute access.  Just by navagating to the folder with your sounds in it with the terminal, and giving  it the:

sudo chown -R peter name_of_directory
and then
sudo chmod -R 777 name_of_directory

should do it.

---

### Post by konungursvia on 2008-03-04
Legolas - thanks.

They already belonged to my "peter" user :(

But I still love linux. I think it's just the Azalia card which needed the backports for sound to work at all.

P

---

