---
title: "streamlink for bbc broadcasts stopped working again."
date: 2019-11-11
forum: Multimedia Software
---

### Post by ajgreeny on 2019-11-11
I used to use streamlink to stream live BBC broadcasts rather than BBC iPlayer in a browser as it was much less resource hungry, playing the stream in VLC, MPV or a player of your choice, and allowed different quality streams.
The command used with no problem was, for example ```
streamlink --bbciplayer-username <*snip-username*> --bbciplayer-password <snip> -p vlc --default-stream 540p_alt2 www.bbc.co.uk/iplayer/live/bbcone
```
Suddenly about 2 or 3 months ago the streams stopped working with various errors appearing
```
[cli][info] Found matching plugin bbciplayer for URL www.bbc.co.uk/iplayer/live/bbcone
[plugin.bbciplayer][info] A TV License is required to watch BBC iPlayer streams, see the BBC website for more information: https://www.bbc.co.uk/iplayer/help/tvlicence
Traceback (most recent call last):
  File "/usr/bin/streamlink", line 11, in <module>
    load_entry_point('streamlink==1.1.1', 'console_scripts', 'streamlink')()
  File "/usr/share/streamlink/streamlink_cli/main.py", line 1033, in main
    handle_url()
  File "/usr/share/streamlink/streamlink_cli/main.py", line 577, in handle_url
    streams = fetch_streams(plugin)
  File "/usr/share/streamlink/streamlink_cli/main.py", line 457, in fetch_streams
    sorting_excludes=args.stream_sorting_excludes)
  File "/usr/lib/python3/dist-packages/streamlink/plugin/plugin.py", line 323, in streams
    ostreams = list(ostreams)
  File "/usr/lib/python3/dist-packages/streamlink/plugins/bbciplayer.py", line 229, in _get_streams
    if not self.login(self.url):
  File "/usr/lib/python3/dist-packages/streamlink/plugins/bbciplayer.py", line 203, in login
    http_nonce = self._extract_nonce(session_res)
  File "/usr/lib/python3/dist-packages/streamlink/plugins/bbciplayer.py", line 116, in _extract_nonce
    final_url = urlparse(last_redirect_query['goto'])
KeyError: 'goto'

```
Anyone else seen this problem, and if so have you figured out a solution to get it working again?

---

### Post by ajgreeny on 2019-11-12
After a lot of  going round in circles searching for an answer I eventually found a workaround from many streamlink "issues" in the thread at [https://github.com/streamlink/streamlink/issues/2607](https://github.com/streamlink/streamlink/issues/2607) done by simply editing /usr/lib/python3/dist-packages/streamlink/plugins/bbciplayer.py.

That sorts out the problem for the BBC but I've discovered that there is also a similar problem with the itvplayer.py, though for itv1 and itv4 only, itv2 and itv3 stream well, so I'll continue searching for an answer to that and will report back if I find a solution.

EDIT:
Yet more info though not a solution.
It seems itv1 and itv4 are DRM so at present must use flash streaming.
Not sure there's an answer to this allowing use of vlc/mpv but will keep looking.

---

### Post by shantiq on 2019-11-20
AJ Sometimes finding skipping streamlink [the middleman]better altogether
these work currently for me put them in my .bashrc

```

alias BBC1='mpv http://a.files.bbci.co.uk/media/live/manifesto/audio_video/simulcast/hls/uk/abr_hdtv/ak/bbc_one_hd.m3u8'
alias BBC2='mpv http://a.files.bbci.co.uk/media/live/manifesto/audio_video/simulcast/hls/uk/abr_hdtv/ak/bbc_two_hd.m3u8'
alias BBC4='mpv http://a.files.bbci.co.uk/media/live/manifesto/audio_video/simulcast/hls/uk/abr_hdtv/ak/bbc_four_hd.m3u8'
```

then obviously save refresh >> ```
. ~/.bashrc
```  then call with BBC1 etc


to test etc ...   [see if it flies your end]


```
mpv http://a.files.bbci.co.uk/media/live/manifesto/audio_video/simulcast/hls/uk/abr_hdtv/ak/bbc_one_hd.m3u8
```


PS   a thorough list [here]("https://gist.githubusercontent.com/random-robbie/e56919b5603ecc87af885391e7331657/raw/65661a4e6fa8c706cc8fe1cf7c553927e5cf62a7/BBC.m3u")

---

### Post by ajgreeny on 2019-11-20
Thanks shantiq.

That does also work for me, and I tried the command using vlc instead of mpv and it also works with that.

Just out of interest how did you manage to find that URL for the streams?  After streamlink stopped working I searched for alternative URLs without any success.

---

### Post by shantiq on 2019-11-20
...just the vagaries of the net AJ  ....    i remember one time the streams stopped working with mpv and you pointed me to streamlink which worked a treat  and thanx again...   then that went belly up after a while  ....   the constant dance of the net :] everything in motion always ....    specifically for those    just luck scouring 6 or more different suggestions from folks on Google until came upon this one ....   been solid here for a year or more but hey touching wood as i speak ....    for the time being tho easier than trudging through streamlink     mpv is my favourite for ALL media these days ...

PS   quite a list he has compiled ...  i mean who knew :]
```
[COLOR=#000000]http://a.files.bbci.co.uk/media/live/manifesto/audio_video/simulcast/hls/uk/hls_tablet/ak/bbc_one_[/COLOR][COLOR=#800000]channel_islands[/COLOR][COLOR=#000000].m3u8[/COLOR]
```

---

### Post by ajgreeny on 2019-11-22
FTR:

Just today (for 18.04) there has been an upgrade of streamlink from 1.1.1+dfsg-1~webupd8~bionic to 1.3.0+dfsg-1~webupd8~bionic.

This new version works out of the box without the need for the edit of /usr/lib/python3/dist-packages/streamlink/plugins/bbciplayer.py.

---

### Post by ajgreeny on 2020-01-04
Well, here we are six weeks on from my last post with streamlink not working again; this is getting a bit boring so I have now reverted to the links you showed in post #3 using VLC which I personally prefer, though mpv also still works fine.

A search has so far found no changes at either BBC or github that might have anything to do with this repeat failure.

---

### Post by shantiq on 2020-01-04
streamlink moving the goalposts?   no changes here

how about cvlc?   if you do not enjoy mpv

---

### Post by ajgreeny on 2020-01-04
Works with **cvlc** as well, perhaps no surprise there, if that's your preference over the graphic window version of vlc.

---

