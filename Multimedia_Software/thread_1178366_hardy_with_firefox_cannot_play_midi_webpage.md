---
title: "hardy with firefox cannot play midi webpage"
date: 2009-06-04
forum: Multimedia Software
---

### Post by kkfok1 on 2009-06-04
Hi,

My problem : not able to play midi file from [http://www.duosuccess.com/TCM/001a01080301b01aj.htm](http://www.duosuccess.com/TCM/001a01080301b01aj.htm)

What I have done : Ubuntu Hardy, firefox 3.0.10, timidity and mozplugger installed, and have delete the plugin.dat under mozilla/firefox as recommended in those threads

Appreciate help :
1. Please let me have another webpage will play midi file once the page loaded to verify if the problem is on the webpage or my installation.

I have visited those pages like [http://nethymnal.org/mid/s/t/c/st_columba.mid](http://nethymnal.org/mid/s/t/c/st_columba.mid), I can play the midi while click on the play button.

2. Appreciate some expert can walk me through the steps to troubleshoot.

I have been working this for the last 5 days and still not working.:(

Many thanks

---

### Post by jerrrys on 2009-06-04
how bout rechecking that link...

---

### Post by kkfok1 on 2009-06-05
I have used Firefox in windows to load the link (duosuccess webpage), the midi was playing without problem.

But I am not able to do this under Ubuntu platform. To troubleshoot whether the problem is with the link (the way Javascript) or Ubuntu, I'll need a webpage that have midi file embedded to confirm this.

---

### Post by kkfok1 on 2009-06-08
Appreciate some expert can help. I need the duosuccess website urgently because the site is providing music therapy.

Thanks

---

### Post by kkfok1 on 2009-06-13
HI,

After some troubleshooting and many googling, I can summarise the following :

1. I can play the midi when the page loaded provided the web page has the following line on the webpage :

<embed src="AskMeWhy.mid" align="baseline" border="1" hidden="false" width="1" height="1" autostart="true" autoplay="true" loop=2><br><br>

2. The midi cannot play if the hidden=true, which means it must have the play button panel being shown.

3. The midi cannot play in the following scenario:

if((MSIE>-1) || (OPER>-1)) {

document.write("<BGSOUND SRC=\"AskMeWhy.mid\" LOOP=10>");

} else {

document.write("<embed src=\"AskMeWhy.mid\" hidden="false" border="0" width="310" height="45" autostart="true" autoplay="true" loop="true" volume="75%">");

}

I am not sure if this causing by timidity or mozplugger or something else.
Can someone please help to shed some light into this ? 

Basically how to play the midi when the page is loaded without to display the play panel under ubuntu/firefox. Because this webpage is access by several browsers and a WMP panel will be shown under IE if the code in 1. is used.

---

### Post by kkfok1 on 2009-06-17
OK, I have solved the problem by modify the mozpluggerrc

vi /etc/mozpluggerrc
search the midi section like below :
audio/mid:midi,mid:MIDI audio file
audio/x-mid:midi,mid:MIDI audio file
audio/midi:midi,mid:MIDI audio file
audio/x-midi:midi,mid:MIDI audio file
	noisy stream: timidity -Os "$file"   <===== take out the word controls
	controls: playmidi "$file"

with the word controls, then the plugin will expect to display the play,pause,stop panel in order to play.

And remember to delete the pluginreg.dat under firefox and restart firefox.

---

