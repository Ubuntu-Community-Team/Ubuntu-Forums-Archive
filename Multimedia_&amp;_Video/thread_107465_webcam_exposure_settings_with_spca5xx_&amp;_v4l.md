---
title: "webcam exposure settings with spca5xx &amp; v4l"
date: 2005-12-23
forum: Multimedia &amp; Video
---

### Post by pinballkid on 2005-12-23
I'm using a Genius VideoCAM that is running under v4l, using the spca5xx kernel module to get it running. It works wonderfully, except that it is horribly bright and I cant see how to change the exposure settings.

Does anyone know how to change exposure settings in either v4l or spca5xx?
Thanks

---

### Post by sham69 on 2006-05-10
I have same problem...can adjust exposure with Windows driver (Logitech Quickcam Traveller), but not in Linux. Outside light too bright, low light too dark...small window of viewing ie brightly lit office only. (this is probably best for most, but I'd like to point cam outside....)
Will check spca5xx site for updates!

---

### Post by MrMozza on 2006-12-31
Web cam/webcam image/picture too bright/white?

I used camE and set lag_reduce to 40 (lag_reduce = 40), this takes multiple grabs and keeps the last - but the important bit is that it gives the web cam a change to automatically adjust the image  brightness. This worked up to a certain brightness but then can do no better (my web cam points outside).

I also found camorama worked as it displays a live preview (not much good for me as I dont always want the desktop/Gnome running).

This worked for my Logitech QuickCam Express (from lsusb):
046d:0870 Logitech, Inc. QuickCam Express

The configuration of camE is rather undocumented - I use it for grabbing a single image via a script, so I use the "temp_file" as the image to keep. I also installed the MS fonts and had to change the font directory referred to in the sample configuration file.

I'm using Ubuntu Edgy Eft 6.10.

I call camE like this:
camE -c /etc/camE.conf -f -s

/etc/camE.info is empty

/etc/camE.conf looks like this:

[ftp]
host = 127.0.0.1
user = camE
pass = camE
dir  = public_html/images
# where should the file end up? Also, this extension determines the file
# type the image is saved as. Try image.png for a png.
file = webcam.jpg
# camE uploads to a temp file, and moves it across when done
# this way people don't view half-uploaded images
tmp  = uploading.jpg
# keep the connection open (1) or reopen it for each shot (0)
keepalive = 1
# do passive ftp?
passive = 1
#an interface to use for non-passive ftp.  use "-" to let libcurl choose, or
#use a real interface name.  (libcurl often chooses incorrectly)
interface = -
# ftp debugging? (noisy)
debug = 0
# Actually do the upload? If do = 0, just take and archive pics.
do = 0
# Some servers require us to explicitly delete the previous image
# In that case, enable this option
delete_first = 0
# Determines how many shots are taken before an image is uploaded.
# (1 == every picture is uploaded, 10 would be every 10th image)
# (Defaults to 1 if not present)
upload_every = 1

# you can set ftp->do to 0 above and use scp instead - you still need
# the dir, file and tmp settings in the ftp section for this to work.
# scp also honors the upload_every setting from the ftp section, and
# will also default to a value of 1 if not present.

[scp]
# target = user@host

[grab]
device = /dev/video0
# store temp image on local machine
temp_file = /var/www/weather/webcam.jpg
# lag reduction, takes 5 shots, discards the first 4, thus clearing mmap
# buffers
lag_reduce = 40
# This goes at the bottom left, with the message from "infofile" appended.
# It is run through strftime, so date vars are expanded.
text   = %d/%m/%Y %H:%M %Z
width  = 352
height = 288
# delay between uploading one shot and starting the next
delay  = 10
# do we want to correct the delay for a slow connect?
# (keeps the perpetually updating clients in sync)
correct = 1
# scale image resolution dynamically based on bandwidth?
# percentage of the delay to spend uploading the image,
# 100 disables, useful values are < 40
percent = 100

########################################################
# PWC specific features (only for philps cams right now)

# framerate of cam capture, lower fps -> less grainy image, more chance or
# blurred motion
framerate = 5

# image settings (0-100)
colour = 50
brightness = 50
contrast = 50
hue = 50
whiteness = 50

# White balance mode
# can be "auto", "indoor", "outdoor", "fluorescent" or "manual"
pwc_wb_mode = auto
# if _mode is set to manual, these two controls affect the balance
# (0-100)
pwc_wb_red = 50
pwc_wb_blue = 50
########################################################


# where to log activity. comment out this line to disable logging
#logfile = /home/gilbertt/.camlog
# gets the message text from here. one line allowed only. means you can do
# stuff like echo "sleeping and stuff" > ~/.caminfo
infofile = /etc/camE.info
# directory to archive pics in. They are datestamped and saved in here.
archive = /opt/images/webcam
# archive pics in datestamped subdirs
# (1 == with subdirs, 0 == without subdirs)
archive_subdirs = 0
# extension (determines type) of archived images.
archive_ext = jpg
# determines how many shots are taken before a pic is archived
# (1 == every pic, 0 == don't archive)
archive_shot_every = 0
# create archive thumbnails enable/disable flag and give width/height
archive_thumbnails_dir    = /opt/images/webcam/thumbnails
archive_thumbnails_create = 1
archive_thumbnails_width  = 120
archive_thumbnails_height = 90
# jpeg quality (you can save as png etc too, but then quality does squat)
quality = 80
input  = 0
# 0 for PAL, 1 for NTSC
norm   = 0
# Goes in the top right. strftime() is run on this too, so put date stuff in
# if you like
title_text = 
# color/transparency of title text
title_r = 255
title_g = 255
title_b = 0
title_a = 255
# font for title text. fontname/size
title_font = arial/8
# fancy font styles
# title_style = /path/to/title.style
# color/transparency of message text
text_r = 255
text_g = 255
text_b = 0
text_a = 255
# font for message text. fontname/size
text_font = arial/8
# fancy font styles
# text_style = /path/to/text.style
# color/transparency of rectangle behind text
# make it 0,0,0,0 to disable.
bg_a = 0
bg_b = 0
bg_g = 0
bg_a = 100
# directory to look for ttf fonts in
#ttf_dir = /usr/X11R6/lib/X11/fonts/TrueType
ttf_dir = /usr/share/fonts/truetype/msttcorefonts
# file to check for before shooting. while this file exists, no shots will
# be taken.
#blockfile = /home/gilbertt/BLOCKCAM
# image to upload when blockfile is first put in place
#offline_image = /home/gilbertt/.block.jpg
# File to check before shotting, while this file exists, shots will be taken.
# but not uploaded. blockimage will not be uploaded if you set this.
#uploadblockfile = /home/gilbertt/BLOCKUPLOAD
# Shots will only be taken/uploaded if the specified interface is active.  
#watch_interface = ppp0
# image to overlay
#overlay_image = /home/gilbertt/.lb.png
#overlay_x = 5
#overlay_y = 5
# do things. like play sounds or whatever. Each is a shell command.
#action_pre_shot
#action_post_shot
#action_post_upload
# image processing
# crop = 1
# crop_width = 320
# crop_height = 240
# crop_x = 20
# crop_y = 20
#
# scaling is applied after cropping, so you can
# remove borders then stretch up the result
# scale = 1
# scale_width = 640
# scale_height = 480
#
# Flip the image horizontally or vertically.
# Horizontal flipping is useful for some Philips cams
# which give a mirrored image when used with the pwc module.
# flip_horizontal = 1
# flip_vertical = 1
#
# Change the orientation of the image.
# Useful if your camera is on its side (for whatever reason).
# 1 rotates clockwise by 90 degrees, 2, rotates clockwise by 180 degrees, 
# 3 rotates clockwise by 270 degrees.
# orientation = 1;

---

