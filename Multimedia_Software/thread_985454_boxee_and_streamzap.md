---
title: "boxee and streamzap"
date: 2008-11-17
forum: Multimedia Software
---

### Post by meg23 on 2008-11-17
If anyone has a streamzap remote working with boxee, can you post your Lircmap.xml? I can't figure out why mine won't work. 

Thanks, mg

---

### Post by dereklee on 2008-12-26
Here's the entry I came up with tonight for the Streamzap remote.  Seems to work just fine.  Add this into the boxee .xml config file.


```
	<remote device="Streamzap_PC_Remote">
		<pause>PAUSE</pause>
		<stop>STOP</stop>
		<forward>&gt;&gt;</forward>
		<reverse>&lt;&lt;</reverse>
		<left>LEFT</left>
		<right>RIGHT</right>
		<up>UP</up>
		<down>DOWN</down>
		<select>OK</select>
		<pageplus>CH_UP</pageplus>
		<pageminus>CH_DOWN</pageminus>
		<back>EXIT</back>
		<menu>MENU</menu>
		<title>PLAY</title>
		<info>More</info>
		<skipplus>&gt;&gt;|</skipplus>
		<skipminus>|&lt;&lt;</skipminus>
		<display>Teletext</display>
		<start>Home</start>
		<record>RECORD</record>
		<volumeplus>VOL_UP</volumeplus>
		<volumeminus>VOL_DOWN</volumeminus>
		<mute>MUTE</mute>
		<power>POWER</power>
		<myvideo>Videos</myvideo>
		<mymusic>Music</mymusic>
		<mypictures>Pictures</mypictures>
		<mytv>TV</mytv>
		<one>1</one>
		<two>2</two>
		<three>3</three>
		<four>4</four>
		<five>5</five>
		<six>6</six>
		<seven>7</seven>
		<eight>8</eight>
		<nine>9</nine>
		<zero>0</zero>
		<mytv>RED</mytv>
		<mymusic>GREEN</mymusic>
		<mypictures>YELLOW</mypictures>
		<myvideo>BLUE</myvideo>
	</remote>

```

---

### Post by rgn5002 on 2009-01-09
is there something I'm missing here?

I installed Lirc through the Synaptic Package Manager and as well as some sort of lirc setup utility which recognized my remote and updated the config file or something. 

Then i went into /opt/boxee/system/lircmap.xml or whatever and added the code posted above.

I rebooted and the remote still will not work.

If someone could please take the time and help me out i would really appreciate it.

---

### Post by Eiht on 2009-08-18
Found somewhere else that you don't want the /opt/boxee/UserData/lircmap.xml

you want to copy that file to ~/.boxee/UserData/    then add the stuff posted above into there.

---

