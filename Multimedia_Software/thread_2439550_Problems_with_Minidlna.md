---
title: "Problems with Minidlna"
date: 2020-03-29
forum: Multimedia Software
---

### Post by wsfield99 on 2020-03-29
Hello, Thanks in advance for your assistance. I also know that you may need additional information to help me resolve this issue. Also. please note that while I am a long time Ubuntu user and enthusiast I am not a programmer so it's best to assume that my understanding of issues is on the level of a technically challenged four year old. That being said: I am attempting to set up a DNLA server to stream media from my LenovoT430 to a Roku XD 2 and an Amazon Firestick. I already have a working setup using an old hp laptop with Xenial Pup installed. The HP has limited capabilities. My Lenovo's main OS is Windows 10. I have Ubuntu 19.04 installed on a VMware 15 player (free version). So far I have downloaded and installed minidlna modified the minidnla.cofig file thus;

media_dir=/home/f/Downloads
media_dir=P,/home/f/Downloads
media_dir=V,/home/f/Downloads
media_dir=PV,/home/f/Downloads
media_dir=/home/f/Downloads

# Set this to merge all media_dir base contents into the root container
# (The default is no.)
#merge_media_dirs=no

# Path to the directory that should hold the database and album art cache.
db_dir=/var/cache/minidlna

# Path to the directory that should hold the log file.
log_dir=/var/log

media_dir=/home/f/Downloads
media_dir=P,/home/f/Downloads
media_dir=V,/home/f/Downloads
media_dir=PV,/home/f/Downloads
media_dir=/home/f/Downloads

# Set this to merge all media_dir base contents into the root container
# (The default is no.)
#merge_media_dirs=no

# Path to the directory that should hold the database and album art cache.
db_dir=/var/cache/minidlna

# Path to the directory that should hold the log file.
log_dir=/var/log

media_dir=/home/f/Downloads
media_dir=P,/home/f/Downloads
media_dir=V,/home/f/Downloads
media_dir=PV,/home/f/Downloads
media_dir=/home/f/Downloads

# Set this to merge all media_dir base contents into the root container
# (The default is no.)
#merge_media_dirs=no

# Path to the directory that should hold the database and album art cache.
db_dir=/var/cache/minidlna

# Path to the directory that should hold the log file.
log_dir=/var/log

media_dir=/home/f/Downloads
media_dir=P,/home/f/Downloads
media_dir=V,/home/f/Downloads
media_dir=PV,/home/f/Downloads
media_dir=/home/f/Downloads

# Set this to merge all media_dir base contents into the root container
# (The default is no.)
#merge_media_dirs=no

# Path to the directory that should hold the database and album art cache.
db_dir=/var/cache/minidlna

# Path to the directory that should hold the log file.
log_dir=/var/log
media_dir=/home/f/Downloads
media_dir=P,/home/f/Downloads
media_dir=V,/home/f/Downloads
media_dir=PV,/home/f/Downloads
media_dir=/home/f/Downloads

# Set this to merge all media_dir base contents into the root container
# (The default is no.)
#merge_media_dirs=no

# Path to the directory that should hold the database and album art cache.
db_dir=/var/cache/minidlna

# Path to the directory that should hold the log file.
log_dir=/var/log

media_dir=/home/f/Downloads
media_dir=P,/home/f/Downloads
media_dir=V,/home/f/Downloads
media_dir=PV,/home/f/Downloads
media_dir=/home/f/Downloads

# Set this to merge all media_dir base contents into the root container
# (The default is no.)
#merge_media_dirs=no

# Path to the directory that should hold the database and album art cache.
db_dir=/var/cache/minidlna

# Path to the directory that should hold the log file.
log_dir=/var/log

media_dir=/home/f/Downloads
media_dir=P,/home/f/Downloads
media_dir=V,/home/f/Downloads
media_dir=PV,/home/f/Downloads
media_dir=/home/f/Downloads

# Set this to merge all media_dir base contents into the root container
# (The default is no.)
#merge_media_dirs=no

# Path to the directory that should hold the database and album art cache.
db_dir=/var/cache/minidlna

# Path to the directory that should hold the log file.
log_dir=/var/log

So, even with restarting the service my new server is not visible on either of my streaming media servers. That's it for now. Scott

---

### Post by TheFu on 2020-03-29
1) Please clean up the post above. We don't need to see the same stuff 20 times. Only about 15 lines above actually matter for the config. posting those lines wrapped in "code tags" would be slightly helpful, BTW.  Code tags are trivial use, but hard to explain: [https://ubuntuforums.org/showthread.php?p=12776168#post12776168](https://ubuntuforums.org/showthread.php?p=12776168#post12776168)

2) Please don't use 19.04. That release lost support in January. Doing anything using it is a mistake. Move to 19.10 with the expectation to move to 20.04 in June.  In July, support for 19.10 ends.  20.04 gets 5 yrs of support.

3) Roku XD 2 doesn't support many popular media codecs.  In general, for video it will support only h.264 with AAC audio. Those files are usually stored inside either .mp4 or .mkv containers.  Audio files can be .aac or mp3. 

Audio Formats: AAC, MP3
Video Formats: H.264, MKV, MPEG-4
Photo Formats:  JPEG, PNG

That means no mpeg2 audio or video are supported.  Do you like DVDs? Hope not, at least not without transcoding to h.264.

4) I wouldn't have media under /home/, but that's a personal decision mainly around OS upgrades and backup plans.

I don't know what codecs a fire stick supports. Sorry.

BTW, I have a Roku3 which has similar codec limitations and will probably upgrade.  In the meantime, I use Plex Server as my DLNA system because it can transcode content to whatever is supported by the player (roku) on-the-fly.  That means all the h.26**5** and older videos from when the kids were younger in avi/divx/mp3 format don't need to be re-encoded just for the Roku to play them back.  For me, the Roku is about playing DRM paid content. For all other content, we use raspberry Pi v2/v3 running OSMC, a Kodi distro designed for R-Pi hardware.

---

### Post by wsfield99 on 2020-03-31
Hello, thanks in advance for your assistance.  I am running Ubuntu 19.10 inside a VMware workstation.  The workstation is installed on a Lenovo T430 that is running Windows 10.  I would like to turn my virtual computer into a media server.  I currently have an old laptop that running Xenialpup which I have been able, with a lot of help, to setup as a server using minidnla.  This server allows me to connect with my smart tv and with a Roku XD 2 and a Firestick.  Thank you.  Scott

---

### Post by TheFu on 2020-03-31
You opened another thread here: [https://ubuntuforums.org/showthread.php?t=2439550](https://ubuntuforums.org/showthread.php?t=2439550)  
Best to have 1 thread going for 1 problem.

The VM needs to be using a "bridged network", not a NAT.
"Servers" need to have static ips.  Set that up.
After that, it becomes just like any server setup.

Above it ways you have miniDLNA working and the TV and Roku connect.

So, what, exactly, is the problem?  I&#8217;m confused.

---

