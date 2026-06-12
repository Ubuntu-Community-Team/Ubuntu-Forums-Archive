---
title: "burning mp3 and ogg to audio cd"
date: 2008-07-24
forum: Multimedia Software
---

### Post by Dutch70 on 2008-07-24
I am getting ready to burn my first cd(audio), I want it to be able to play in a car cd player. I have searched the boards and found some good info,(about K3b & mp3's) but still have a couple questions about .ogg

I am going to use K3b, some of the songs are mp3, and some are .ogg.
Will K3b burn both mp3 and .ogg files to the same cd and still play in a car type cd player, and is there anything else I should look out for, so to speak?

I have only burned one cd before period, and that was using power2go in vista. 

Also are there any cd label making programs for linux, or even something that will make use of lightscribe.

---

### Post by ajgreeny on 2008-07-24
You should have no problem burning a disk of audio using either brasero or k3b in Ubuntu, and it will make no difference which file type the original happened to be, mp3, ogg, wav, etc etc, it doesn't matter at all.  Just make sure you use a CD-R, not CD-RW as they often will not play in car stereos.

Can't help with label printers or using lightscribe, I'm afraid, but I'll bet it's possible.

---

### Post by Dutch70 on 2008-07-24
Thanks ajgreeny, I tried it, and k3b said I had to convert it to wav files, so I tried brasero and it is giving the error "**resource not found**" when I click on "**view log**" this is what I get if anyone cares to look...

```
Checking session consistency (brasero_burn_check_session_consistency burn.c:1714)
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_M22LEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_3I3LEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_533LEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_OY3LEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_DD1LEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_450LEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_YQ1LEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_TK1LEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_E71LEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_2U1LEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_JG2LEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_HA2LEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_SCTLEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_M6SLEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_9TTLEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_SLTLEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_J7TLEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_Q1TLEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_WNULEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_MHULEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_1XRLEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_1QRLEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_7BSLEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_85RLEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_3ZRLEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_ILSLEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack Output set (AUDIO) image = /tmp/brasero_tmp_8DSLEU.cdr
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode deactivating
BraseroTranscode called brasero_job_get_action
BraseroTranscode Output set (AUDIO) image = /tmp/brasero_tmp_QLWLEU.cdr
BraseroTranscode called brasero_job_get_session_output_size
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_set_use_average_rate
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_done_tracks
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode settings track boundaries time = 0 212270952380 / bytes = 0 37444596
BraseroTranscode Creating new pipeline
BraseroTranscode called brasero_job_get_current_track
BraseroTranscode called brasero_job_get_action
BraseroTranscode called brasero_job_get_fd_out
BraseroTranscode called brasero_job_get_image_output
BraseroTranscode gstfilesrc.c(977): gst_file_src_start (): /pipeline3/filesrc49:
No such file "/home/david/Music/DD's CD 2/Clay Walker - Fall.mp3"
BraseroTranscode called brasero_job_error
BraseroTranscode finished with an error
BraseroTranscode asked to stop because of an error
	error		= 3
	message	= "Resource not found."
BraseroTranscode stopping
Session error : Resource not found. (brasero_burn_record burn.c:2270)
```

I really want to get this straightened out, so I'll be one step closer to a windows free world. 
I've got one step up on a lot of people though, in that I dont know much about windows either...:lolflag: (just a joke, but true)

Just out of curiousity will vista burn .ogg files to an audio cd. in case I dont get this fixed soon? Because I am making this cd for my fiance who is flying in today. :lol:

---

### Post by pmlxuser on 2008-07-24
> **Dutch70 said:**
> e)

Just out of curiousity will vista burn .ogg files to an audio cd. in case I dont get this fixed soon? Because I am making this cd for my fiance who is flying in today. :lol:

it depends which program you want to use for the burning by default Window$ Media Player does not play .ogg and i don't think will burn .ogg by default without installing extra codes

last time i used windows vista though with NERO (forgotten the version) you could.

---

### Post by ajgreeny on 2008-07-24
Have you got all the codecs you need for this?  For k3b you need to have libk3b2-extracodecs installed; for brasero you'll need the gstreamer0.10-fluendo-mp3 package, and no doubt many other gstreamer plugins  as well in order to get all the files to burn as an audio disk.  I am presuming you are able to play mp3 and ogg files already.

---

