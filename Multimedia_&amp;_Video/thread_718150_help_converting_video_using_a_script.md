---
title: "help converting video using a script"
date: 2008-03-07
forum: Multimedia &amp; Video
---

### Post by Nikhil Gohil on 2008-03-07
i m using a script to convert videos for my n95 mobile. i have a problem that in some of my videos, after converting there is too much space for the black bars top and bottom of the video. i was wondering if there was any way to remove the black bars? also in some videos the video lags the audio. can i set any offset while converting? im quite new to ubuntu. if someone could suggest a change to the script or any other way to convert, it will help a lot. also, could someone suggest a gui to do this?

```
require 'getoptlong'

DEFAULT_ARGS = "-f mp4 -vcodec xvid -maxrate 1000 -qmin 3 -qmax 5 -bufsize 4096 -g 300 -acodec aac"
DEFAULT_AUDIO_BITRATE = 128
DEFAULT_VIDEO_BITRATE = 250
WIDTH = 320.0
HEIGHT = 240.0

$options = {}
opts = GetoptLong.new(
  [ "-a", GetoptLong::REQUIRED_ARGUMENT ],      # audio bitrate
  [ "-h", GetoptLong::NO_ARGUMENT ],            # help
  [ "-b", GetoptLong::REQUIRED_ARGUMENT ],      # video bitrate
  [ "-v", GetoptLong::NO_ARGUMENT ]             # verbose
)
opts.each { |opt, arg| $options[opt] = arg }

if $options['-h']
  puts <<EOF
mp4ize - encode videos to mp4 for an iPod

Usage: mp4ize file1.avi [file2.mpg [file3.asf [...]]]


Options:

  -h       : this help
  -v       : verbose
  -a RATE  : override default audio bitrate (#{DEFAULT_AUDIO_BITRATE})
  -b RATE  : override default video bitrate (#{DEFAULT_VIDEO_BITRATE})
EOF
  exit
end

audio_bitrate = $options['-a'] || DEFAULT_AUDIO_BITRATE
video_bitrate = $options['-b'] || DEFAULT_VIDEO_BITRATE

ARGV.each do |infile|
  outfile = infile.dup
  ext = File.extname(outfile)
  outfile.sub!(/#{ext}$/, '.mp4')

  # open the file to figure out the aspect ratio
  w, h = nil, nil
  IO.popen("ffmpeg -i '#{infile}' 2>&1") do |pipe|
    pipe.each_line do |line|
      puts line
      if line.match(/Video:.+ (\d+)x(\d+)/)
        w, h = $1.to_f, $2.to_f
      end
    end
  end

  begin
    aspect = w/h
  rescue
    puts "Couldn't figure out aspect ratio."
    exit
  end

  height = (WIDTH / aspect.to_f).to_i
  height -= 1 if height % 2 == 1
  pad = ((HEIGHT - height.to_f) / 2.0).to_i
  pad -= 1 if pad % 2 == 1

  File.unlink(outfile) if File.exists?(outfile)
  cmd = "ffmpeg #{DEFAULT_ARGS} -i '#{infile}' -s #{WIDTH.to_i}x#{height} -padtop #{pad} -padbottom #{pad} -ab #{audio_bitrate} -b #{video_bitrate} '#{outfile}'"
  puts cmd if $options['-v']
  system cmd
end 
```

---

### Post by stooshbunutu on 2008-03-11
gui for converting vido to mobile, assuming its 3gp format.

[http://www.miksoft.net/mobileMediaConverter.htm](http://www.miksoft.net/mobileMediaConverter.htm)

it works great for me but has limited input codecs (.flv .mpeg .mpg .wmv)

so might require another conversion as a stepping stone

winff from [http://www.biggmatt.com/winff](http://www.biggmatt.com/winff) requires only ffmpeg
```
sudo apt-get install ffmpeg
```

---

