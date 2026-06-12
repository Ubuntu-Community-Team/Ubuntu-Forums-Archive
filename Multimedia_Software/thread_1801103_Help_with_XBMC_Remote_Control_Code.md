---
title: "Help with XBMC Remote Control Code"
date: 2011-07-09
forum: Multimedia Software
---

### Post by msherman123 on 2011-07-09
Hello all.  Quick question for anyone that is versed w/ the remote control codes for xmbmc.  I am using my XBOX 360 Universal Remote with xbmc on Ubuntu 11.04.  It is working great except for the function to bring me back to the main dashboard.  Previously, this was done by passing the "Start" button string.  Seems to not work now.  Anyone seen this?

Lircmap.xml
```
lircmap>
			<remote device="Microsoft_Xbox360">
				<left>LeftArrow</left>
				<right>RightArrow</right>
				<up>UpArrow</up>
				<down>DownArrow</down>
				<select>OK</select>
				<back>Back</back>
				<forward>FastForward</forward>
      				<reverse>Rewind</reverse>
				<play>Play</play>
				<pause>Pause</pause>
      				<stop>Stop</stop>
				<volumeplus>VolUp</volumeplus>
				<volumeminus>VolDown</volumeminus>
				<mute>Mute</mute>
				<pageminus>PgDown</pageminus>
				<pageplus>PgUp</pageplus>
				<zero>0</zero>
				<one>1</one>
				<two>2</two>
				<three>3</three>
				<four>4</four>
				<five>5</five>
				<six>6</six>
				<seven>7</seven>
				<eight>8</eight>
				<nine>9</nine>
				<power>OnOff</power>
				<skipplus>Next</skipplus>
				<skipminus>Prev</skipminus>
				<display>Display</display>
				<record>Record</record>
				<start>Start</start>
				<info>Info</info>
				<menu>DVD_Menu</menu>
				<myvideo>Y</myvideo>
				<mymusic>X</mymusic>
				<mypictures>A</mypictures>
				<hash>B</hash>
				<clear>Clear</clear>
				<myTV>Enter</myTV>
			</remote>
</lircmap>
```


Keymap.xml
```

<keymap>
	<global>
		<remote>
			<left>Left</left>
			<right>Right</right>
			<up>Up</up>
			<down>Down</down>
			<select>Select</select>
			<back>ParentDir</back>
			<forward>FastForward</forward>
      			<reverse>Rewind</reverse>
			<play>Play</play>
      			<pause>Pause</pause>
      			<stop>Stop</stop>
			<mute>Mute</mute>
			<pageplus>PageUp</pageplus>
      			<pageminus>PageDown</pageminus>
			<volumeplus>VolumeUp</volumeplus>
      			<volumeminus>VolumeDown</volumeminus>
			<zero>Number0</zero>
			<one>Number1</one>
			<two>Number2</two>
			<three>Number3</three>
			<four>Number4</four>
			<five>Number5</five>
			<six>Number6</six>
			<seven>Number7</seven>
			<eight>Number8</eight>
			<nine>Number9</nine>
			<power>XBMC.ShutDown()</power>
			<skipplus>SkipNext</skipplus>
			<skipminus>SkipPrevious</skipminus>
			<display>FullScreen</display>
			<record>Screenshot</record>
			<start>XBMC.ActivateWindow(PlayerControls)</start>
			<info>Info</info>
			<menu>ContextMenu</menu>
			<myvideo>myvideo</myvideo>
			<mymusic>mymusic</mymusic>
			<mypictures>mypictures</mypictures>
			<hash>AspectRatio</hash>
			<clear>ZoomIn</clear>
			<myTV>ZoomOut</myTV>
		</remote>
	</global>
</keymap>
```

---

