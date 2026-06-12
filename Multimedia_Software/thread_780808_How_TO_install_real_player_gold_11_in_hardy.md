---
title: "How TO install real player gold 11 in hardy"
date: 2008-05-03
forum: Multimedia Software
---

### Post by Afif K fiska on 2008-05-03
Just wanna share my little experience in installing real player. cause i've just installed it in my computer, ok, here the step :

1. Download the .bin file in [here]("http://www.real.com/realcom/R?href=http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.bin"), if this link is corrupt, just go to the [http://www.real.com/linux](http://www.real.com/linux)  , download the . bin file there

2. After that, open your terminal, and change your directory to the bin file you've downloaded (using cd command). in my case, i save my download file to directory home/alyapc/Download, here is the example : (from the first time i open terminal)

first  time open the terminal :
> alyapc@alyapc-laptop

here, the cd command :
> alyapc@alyapc-laptop:~$ cd Download

look up the contain of the folder using dir command:
> alyapc@alyapc-laptop:~/Download$ dir
RealPlayer11GOLD.bin

3. Make the file bin executable by using this code :

> chmod a+x RealPlayer11GOLD.bin

4. Then, type this code : (still in the bin containing directory)

> sudo ./RealPlayer11GOLD.bin dont forget the (.) in front after the sudo

5. enter your password

6. follow the instruction (it's a very easy instruction, if u can't get what the instruction mean, just press ENTER in every section)

7. Then Complete!!!! check the real media player in application->sound and video->realplayer11

It's very easy....now i can play a lot of stuff in my hardy..:KS

---

### Post by shaneblues on 2008-05-04
As  someone that as of today is trying to use Ubuntu for every day tasks could you please explain that again and please keep in mind lots of new users have never run more that a ping command in the windows CMD, i know i am really asking for someone to hold my hand but every guide I read assumes that I already know something about the command line and the correct place to save a .bin file, all I want to do is listen to streaming radio from the BBC currently when i try it comes over in compleet garbage. Thanks, Shane

---

### Post by lancern on 2008-05-04
One thing I have noticed about realplayer 11 is that when it is open it uses 100% of the CPU..even if its not playing media..I used the .deb that someone made and posted here..other players only use around 20 to 30% of the cpu when there playing media..that is if the System Monitor is accurate in Xubuntu 8.04...

Edit:
I tried your way and it works..In step 3 the Gold needs to be in all upper case letters..
but even with this install its eating 100% cpu...

---

### Post by Afif K fiska on 2008-05-05
> **shaneblues said:**
> As  someone that as of today is trying to use Ubuntu for every day tasks could you please explain that again and please keep in mind lots of new users have never run more that a ping command in the windows CMD, i know i am really asking for someone to hold my hand but every guide I read assumes that I already know something about the command line and the correct place to save a .bin file, all I want to do is listen to streaming radio from the BBC currently when i try it comes over in compleet garbage. Thanks, Shane

place for the .bin file is up to u, where ever u save it, it doesn't matter. The important thing is cd command. CD means changing your directory to the directory written after the CD command. here is the example

if i wrote : cd home , means that directory under my control now is home  

this command work if the subfolder name home exist in the upper directory

For streaming radio, maybe you should look in another section, cause i never do that. sory, hope this will help

---

### Post by Afif K fiska on 2008-05-05
> **lancern said:**
> One thing I have noticed about realplayer 11 is that when it is open it uses 100% of the CPU..even if its not playing media..I used the .deb that someone made and posted here..other players only use around 20 to 30% of the cpu when there playing media..that is if the System Monitor is accurate in Xubuntu 8.04...

Edit:
I tried your way and it works..In step 3 the Gold needs to be in all upper case letters..
but even with this install its eating 100% cpu...

Thanks for your correction, i've change it.
I install it in ubuntu, and after running system monitor, it's only show about 20 - 30 % cpu works. Maybe something wrong with your Xubuntu system monitor

---

### Post by presston on 2008-05-05
note that it don't support avi, wmv etc video.

---

### Post by Afif K fiska on 2008-05-05
> **presston said:**
> note that it don't support avi, wmv etc video.
 yes you're right, i combine it with VLC, it become a deadfull tools for video player...:)

---

### Post by minus1 on 2008-05-06
Thankyou, I needed Real Player to listen to online radio.This was a great help.

---

### Post by lazydesi on 2008-05-08
good work mate

---

