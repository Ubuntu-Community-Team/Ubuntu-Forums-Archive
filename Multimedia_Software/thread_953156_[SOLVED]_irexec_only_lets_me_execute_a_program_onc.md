---
title: "[SOLVED] irexec only lets me execute a program once"
date: 2008-10-19
forum: Multimedia Software
---

### Post by Sin@Sin-Sacrifice on 2008-10-19
So I installed lirc and set up the rc and configured everything to work pretty well. So then I wanted to open programs with the remote... worked well... until I closed the program and then tried to open it again. I set the "music" button on the remote to open rhythmbox and then the "back" button to close it. I also set "irexec &" to run at startup. I started up rhythmbox using the music button... played a few songs and then closed it when there was a knock at my door. A few moments later the guest left and I wanted to start her back up. So I hit the music button again and nothing happened. I alt-F2'd irexec again and hit the music button... worked. I closed rhythmbox immediately and hit it again.... nothing. I also manually clicked open rhythmbox and the irexec let me close it using back but still wouldn't let me start it back up until I restarted irexec. Anyone else have this problem? 
I'm using an HP assigned windows mce remote with a usb receiver and Ubuntu Gutsy.

---

### Post by Sin@Sin-Sacrifice on 2008-10-22
please.... it's driving me nuts here.

---

### Post by Sin@Sin-Sacrifice on 2008-10-23
Alright... so I figured it out on my own once again. Glad that someone can. Regardless... the problem was with how lircrc was written. I didn't know it but the mode of which the remote goes into when I press a button to use irexec to start a program is the only mode the software knows thereafter unless you tell it otherwise. I had it so when I pressed the "music" button rhythmbox started and then "back" closed it. Little did I know that it was still in rhythmbox mode. I needed to tell it to go back into irexec mode so I could start rhythmbox or whatever other program I wanted again. The original lircrc was ```
begin
  prog = irexec
  button = music
  config = rhythmbox &
  mode = rhythmbox
end
begin
	prog = irexec
	button = back
	config = killall rhythmbox
end
begin
	prog = irexec
	button = videos
	config = mplayer
	mode = mplayer
end
begin
	prog = irexec
	button = back
	config = killall mplayer
	mode = irexec
end
############################
####MPlayer controls###########
############################
begin
	prog = mplayer
	button = mute
	config = mute
end
begin
	prog = mplayer
	button = pause
	config = pause
end
begin
	prog = mplayer
	button = play
	config = seek +0
end
begin
	prog = mplayer
	button = stop
	config = quit
end
begin
	prog = mplayer
	button = exit
	config = get_time_pos
	#config = get_property stream_pos
end
begin
	prog = mplayer
	button = exit
	config = quit
end
begin
	prog = mplayer
	button = power
	config = quit
end
begin
	prog = mplayer
	button = next
	config = seek_chapter +1 0
end
begin
	prog = mplayer
	button = prev
	config = seek_chapter -1 0
end
begin
	prog = mplayer
	button = home
	config = osd 3
	config = osd 1
end
begin
	prog = mplayer
	button = radio
	config = switch_ratio 1.77778
	config = switch_ratio 1.33
end
begin
	prog = mplayer
	button = red
	config = vobsub_lang 1
	config = vobsub_lang
end
begin
	prog = mplayer
	button = forward
	config = seek +30
end
begin
	prog = mplayer
	button = rewind
	config = seek -10
end
begin
	prog = mplayer
	button = right
	config = seek +30
end
begin
	prog = mplayer
	button = left
	config = seek -10
end
begin
	prog = mplayer
	button = chanup
	config = audio_delay 0.1
end
begin
	prog = mplayer
	button = chandown
	config = audio_delay -0.1
end
begin
	prog = mplayer
	button = blue
	config = osd_show_property_text "${filename}" 2400
	config = osd_show_text ""
end

###############################################
### Rhythmbox juke box player 
###############################################

begin
    prog   =    Rhythmbox
    button =    power
    config =    quit
    flags  =    mode
end

begin
    prog = Rhythmbox
    button = play
    config = play
end

begin
    prog = Rhythmbox
    button = pause
    config = pause
end

begin
    prog = Rhythmbox
    button = stop
    config = stop
end

begin
    prog = Rhythmbox
    button = volup
    config = volume_up
    repeat = 3
end


begin
    prog = Rhythmbox
    button = voldown
    config = volume_down
    repeat = 3
end
begin
    prog = Rhythmbox
    button = skip
    config = next
end

begin
    prog = RhythmBox
    button = replay
    config = previous
end

begin
    prog = RhythmBox
    button = mute
    config = mute
end

begin
    prog = RhythmBox
    button = up
    config = shuffle
end

begin
    prog = RhythmBox
    button = down
    config = repeat
end

begin
    prog = RhythmBox
    button = forward
    config = seek_forward
end

begin
    prog = RhythmBox
    button = rewind
    config = seek_backward
end
``` and it needed to be ```
# MAIN BEGIN (irexec mode) - Application Selection Mode
# ---------------

begin irexec
	begin
		prog = irexec
		remote = mceusb
		button = music
		# Start rhythmbox
		config = rhythmbox &
		# Enter rhythmbox mode
		mode = rhythmbox
	end
	begin
		prog = irexec
		remote = mceusb
		button = videos
		# Start mplayer mode
		config = mplayer
		# Enter mplayer mode
		mode = mplayer
	end
end irexec

# rhythmbox mode
begin rhythmbox
	begin
		prog = irexec
		button = back
		config = killall rhythmbox
		mode = irexec
	end
end rhythmbox

# mplayer mode
begin mplayer
	begin
		prog = irexec
		button = back
		config = killall mplayer
		# Enter irexec mode
		mode = irexec
	end
end mplayer
############################
####MPlayer controls###########
############################
begin
	prog = mplayer
	button = mute
	config = mute
end
begin
	prog = mplayer
	button = pause
	config = pause
end
begin
	prog = mplayer
	button = play
	config = seek +0
end
begin
	prog = mplayer
	button = stop
	config = stop
end
begin
	prog = mplayer
	button = next
	config = seek_chapter +1 0
end
begin
	prog = mplayer
	button = prev
	config = seek_chapter -1 0
end
begin
	prog = mplayer
	button = home
	config = osd 3
	config = osd 1
end
begin
	prog = mplayer
	button = radio
	config = switch_ratio 1.77778
	config = switch_ratio 1.33
end
begin
	prog = mplayer
	button = two
	config = vobsub_lang 1
	config = vobsub_lang
end
begin
	prog = mplayer
	button = forward
	config = seek +30
end
begin
	prog = mplayer
	button = rewind
	config = seek -10
end
begin
	prog = mplayer
	button = right
	config = seek +30
end
begin
	prog = mplayer
	button = left
	config = seek -10
end
begin
	prog = mplayer
	button = chanup
	config = audio_delay 0.1
end
begin
	prog = mplayer
	button = chandown
	config = audio_delay -0.1
end

##DVD menu

begin
    remote = mceusb
    prog   = mplayer
    button = Back
    config = q
end

begin
    remote = mceusb
    prog   = mplayer
    button = OK
    config = Space
end

begin
    remote = mceusb
    prog   = mplayer
    button = More
    config = OSD
end

begin
    remote = mceusb
    prog   = mplayer
    button = Left
    config =
end

begin
    remote = mceusb
    prog   = mplayer
    button = Right
    config =
end

begin
    remote = mceusb
    prog   = mplayer
    button = Up
    config =
end

begin
    remote = mceusb
    prog   = mplayer
    button = Down
    config =
end

###############################################
### Rhythmbox juke box player 
###############################################

begin
    prog = Rhythmbox
    button = play
    config = play
end

begin
    prog = Rhythmbox
    button = pause
    config = pause
end

begin
    prog = Rhythmbox
    button = stop
    config = stop
end

begin
    prog = Rhythmbox
    button = volup
    config = volume_up
    repeat = 3
end


begin
    prog = Rhythmbox
    button = voldown
    config = volume_down
    repeat = 3
end
begin
    prog = Rhythmbox
    button = skip
    config = next
end

begin
    prog = RhythmBox
    button = replay
    config = previous
end

begin
    prog = RhythmBox
    button = mute
    config = mute
end

begin
    prog = RhythmBox
    button = up
    config = shuffle
end

begin
    prog = RhythmBox
    button = down
    config = repeat
end

begin
    prog = RhythmBox
    button = forward
    config = seek_forward
end

begin
    prog = RhythmBox
    button = rewind
    config = seek_backward
end
``` And to be completely honest I didn't figure it out myself entirely... it was with the help of about 250 posts I found around the internet. Hope this will help others.

---

