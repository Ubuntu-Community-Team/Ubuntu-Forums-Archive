---
title: "h264 transcode script problem with utcisoformat"
date: 2016-01-17
forum: Mythbuntu
---

### Post by philben on 2016-01-17
I've been using the Mythbuntu Linux implementation of MythTV as a  backend to multiple Kodi frontends. It's been great for serving up live  and recorded broadcasts from my HD Homerun. Now I'd like to start  transcoding some of my recordings to h264. I've been trying to get the  transcode-h264.py script on MythTV's site at [https://www.mythtv.org/wiki/Transcode_Mpeg2_to_H264](https://www.mythtv.org/wiki/Transcode_Mpeg2_to_H264)  to work. I can't get it to run because it doesn't like the use of  utcisoformat in the script. As I understand it that line of the script  is converting the local start time of the recording to the UTC time.  This is the error that's produced:

```
Traceback (most recent call last):
  File "./transcode-h264.py", line 149, in <module>
    main()
  File "./transcode-h264.py", line 143, in main
    runjob(chanid=opts.chanid, starttime=opts.starttime)
  File "./transcode-h264.py", line 40, in runjob
    starttime = str(starttime.utcisoformat().replace(u':', '').replace(u' ', '').replace(u'T', '').replace('-', ''))
AttributeError: 'int' object has no attribute 'utcisoformat'
```

I've tried search variations on python, mythtv and utcisoformat but I  can't find where that attribute is defined. As a test I commented out  the utcisoformat line and hardcoded the UTC value it should have  produced (ex. 20160109193700). With that I successfully transcoded a recording and  I could see and play the transcoded video through my Kodi frontend.  That's telling me I supplied the correct parameters to the script. As an  example these are the parameters I used for the test:

```
./transcode-h264.py --chanid=1021 --starttime=20160109133700 --verbose all
```

I don't know python well so I don't know if utcisoformat is supposed to come from a python library, a mythtv library or something else. Could it be something about the default configuration of python with Mythbuntu? Another alternative is to use a different method to convert the starttime parm fed to the script (ex. 20160109133700) to the UTC time (ex. 20160109193700). In other words, +6 from my locale to get UTC. Your help would be appreciated.

---

### Post by blm-ubunet on 2016-01-19
Wiser folk have revealed that utcisoformat is function defined in MythTV python code..
Shame the script doesn't check/warning about the mythtv python library version.

---

