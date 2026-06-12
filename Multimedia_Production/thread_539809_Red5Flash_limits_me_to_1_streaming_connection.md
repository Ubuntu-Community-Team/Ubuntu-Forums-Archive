---
title: "Red5/Flash limits me to 1 streaming connection"
date: 2007-08-31
forum: Multimedia Production
---

### Post by etechship on 2007-08-31
I have a red5 streaming server, newest version, and I am unable to stream to more than 1 computer at the same time, which is kinda dumb.

I using the oflaDemo stream, so I don't know if that has something to do with it.

here is my flash actionscript:

```

//beginning setttings
stop();
play_pause.label = 'Loading';

//start Netstream
nc = new NetConnection();
nc.onStatus = function(info) {
		if (info.code == "NetConnection.Connect.Success") {
			startstop_pb.enabled = true;
			createNetStream(this);
		}
}

//start XML
tuteInfo_xml = new XML();
tuteInfo_xml.ignoreWhite = true;
tuteInfo_xml.load('http://ucstreaming.net/player/playlist_xml.php');
tuteInfo_xml.onLoad = function(success) {
        if (success) {
                the_path = tuteInfo_xml.firstChild.attributes.location;
				stream_type = tuteInfo_xml.firstChild.attributes.type;
				host = tuteInfo_xml.firstChild.attributes.host;
				stream = tuteInfo_xml.firstChild.attributes.stream;
				nc.connect("rtmp://" +  host + "/" + stream);
		};
};


move_dot = true;

//start playing video
createNetStream = function(nc){
	ns = new NetStream(nc);
	ns.setBufferTime(5);
	ns.play(the_path);//the_path
	screen_video.attachVideo(ns);
	file_name_txt.text = tuteInfo_xml.firstChild.attributes.title;
	ns.onMetaData = monMetaData;
	play_pause.label = 'Pause';
}

//Total video time
function monMetaData(obj:Object){
	totaltxt.text = '/ ' + Math.floor((obj.duration / 60)) +":"+Math.floor((((obj.duration / 60) - Math.floor((obj.duration / 60)))* 60));
	total = obj.duration
}

//When you push on the button ...
play_pause.onRelease = function(){
	ns.pause();
	if (play_pause.label == 'Pause'){
		play_pause.label = 'Play';
	} else if (play_pause.label == 'Play'){
		play_pause.label = 'Pause';
	}
}

//Time Played
onEnterFrame = function(){
	time.text =  Math.floor((ns.time / 60)) +":"+Math.floor((((ns.time / 60) - Math.floor((ns.time / 60)))* 60));
	if (move_dot){
		seek._x =  ((ns.time / total) * 288)+10;
		buffer._x = ((ns.time / total) * 288)+13;
		buffer._y = 283;
		buffer._width = ((ns.bufferLength / total) * 288);
	}
}

//When you move the scrubber slider
var start_drag_right = vol_rail._width + 10;

seek.onPress = function() {
	startDrag(this,true, 10, 283, 302, 283);
	move_dot = false;
}
seek.onRelease= function(){
	stopDrag();
	move_dot = true;
	ns.seek((seek._x * (total / 288)));
}
seek.onReleaseOutside= function(){
	stopDrag();
	move_dot = true;
	ns.seek((seek._x * (total / 288)));
}

```

you can also tell me what to do better with my actionscript, because I am fairly new to this.

thanks

---

