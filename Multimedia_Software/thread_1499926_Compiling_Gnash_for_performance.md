---
title: "Compiling Gnash for performance"
date: 2010-06-02
forum: Multimedia Software
---

### Post by goseph on 2010-06-02
Hi everybody!

My friend has a mere 190MiB of memory and no money for upgrading and she is absolutely sick of the snail-speed windows XP so I am sorting her out with a dual boot with a view to becoming a full time LUbuntu-girl.

The main issue that I anticipate is flash. My slightly better laptop can only just about handle youtube with the adobe plug-in for Linux.

My question is - is compiling with lots of CFlags a possibility for getting youtube to work ok on an old laptop under Lubuntu?

If not, does anybody have any other suggestions?

---

### Post by goseph on 2010-06-02
I do of course mean the flash browser plug-in :)

---

### Post by lovinglinux on 2010-06-02
Install [FlashVideoReplacer](http://flvideoreplacer-extension.blogspot.com). It works for Youtube, Vimeo and Blip.tv, although I will add more sites soon. It doesn't work on YouTube channels yet, just regular videos.

---

### Post by goseph on 2010-06-02
That looks freakin' awesome! Are there any benchmarks? Would you like me to do some?

---

### Post by lovinglinux on 2010-06-02
> **goseph said:**
> That looks freakin' awesome! Are there any benchmarks? Would you like me to do some?

Thanks, but there is no need. Using a plugin like totem or gecko-mediaplayer is a lot less CPU intensive than flash.

---

### Post by goseph on 2010-06-03
Whilst I have your attention, can I make a feauture request for the BBC iPlayer :D

Youtube is actually tolerable but iPlayer seems to be much heavier and jumpier.

---

### Post by lovinglinux on 2010-06-03
> **goseph said:**
> Whilst I have your attention, can I make a feauture request for the BBC iPlayer :D

Youtube is actually tolerable but iPlayer seems to be much heavier and jumpier.

Yes you can, but I'm not sure I will be able to do it. The bigger problem is that I need to see the code of the player page to introduce the compatibility layer in my extension. Unfortunately, sites like that can only be viewed by IP addresses located in the same country as the site. Since I live in Brazil, I can't reach Hulu, ABC, BBC and such (at least by normal means).

---

### Post by goseph on 2010-06-04
> **lovinglinux said:**
> Yes you can, but I'm not sure I will be able to do it. The bigger problem is that I need to see the code of the player page to introduce the compatibility layer in my extension. Unfortunately, sites like that can only be viewed by IP addresses located in the same country as the site. Since I live in Brazil, I can't reach Hulu, ABC, BBC and such (at least by normal means).

Does this help? :) This is page source when a random show is playing, for the iPlayer

```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd"> 
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en-GB" lang="en-GB"> 
<head profile="http://dublincore.org/documents/dcq-html/"> 
	<title>BBC iPlayer - The Culture Show: 2010/2011: Episode 4</title> 
 
	<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" /> 
	<meta name="description" content="Watch The Culture Show: 2010/2011: Episode 4 " /> 
	<meta name="keywords" content="The Culture Show: 2010/2011: Episode 4" /> 
 
	<link rel="schema.DCTERMS" href="http://purl.org/dc/terms/" /> 
	<meta name="DCTERMS.created" content="2008-07-27" /> 
	<link rel="canonical" href="http://www.bbc.co.uk/iplayer/episode/b00snb6w/The_Culture_Show_2010_2011_Episode_4/" />	
	
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
	
	
	
 
 
 
 
 
 
 
 
 
 
	
	
<!-- Glow cachebust:    
                -->   <!-- Barlesque 1.1.5 -->      <link rel="schema.dcterms" href="http://purl.org/dc/terms/" /> <link rel="index" href="http://www.bbc.co.uk/a-z/" title="A to Z" /> <link rel="help" href="http://www.bbc.co.uk/help/" title="BBC Help" /> <link rel="copyright" href="http://www.bbc.co.uk/terms/" title="Terms of Use" /> <link rel="icon" href="http://www.bbc.co.uk/favicon.ico" type="image/x-icon" /> <meta name="viewport" content="width = 974" />          <link rel="stylesheet" type="text/css" href="http://static.bbc.co.uk/frameworks/barlesque/1.1.5/newnav/style/main.css"  /> 
       <script type="text/javascript" src="http://node1.bbcimg.co.uk/glow/gloader.0.1.3.js"> gloader.use("glow", {map: "http://node1.bbcimg.co.uk/glow/glow/map.1.7.3.js"}); </script>     <script type="text/javascript" src="http://static.bbc.co.uk/frameworks/barlesque/1.1.5/newnav/script/blq_core.js"></script> 
  <!--[if (IE 6)|(IE 7)]> <style type="text/css"> html{font-size:125%} body{font-size:50%} #blq-container{float:left} .blq-tooltipped:hover {background-position:0 0} #blq-autosuggest ul li { zoom:normal; } </style> <![endif]--> <!--[if IE 7]> <style type="text/css"> .blq-clearfix {display: inline-block} </style> <![endif]-->  <!--[if IE 6]> <link rel="stylesheet" href="http://static.bbc.co.uk/frameworks/barlesque/1.1.5/newnav/style/ie6.css" type="text/css" /> <style type="text/css"> .blq-js #blq-nav-links-inner {filter:progid:DXImageTransform.Microsoft.AlphaImageLoader(src='http://static.bbc.co.uk/frameworks/barlesque/1.1.5/newnav/img/panel.png', sizingMethod='crop')} .blq-js #blq-nav-foot div {filter:progid:DXImageTransform.Microsoft.AlphaImageLoader(src='http://static.bbc.co.uk/frameworks/barlesque/1.1.5/newnav/img/panel.png', sizingMethod='image');margin-top:-139px} #blq-mast-home span.blq-home { filter:progid:DXImageTransform.Microsoft.AlphaImageLoader(enabled=true, sizingMethod='crop', src='http://static.bbc.co.uk/frameworks/barlesque/1.1.5/newnav/img/blocks.png');} </style>  <script type="text/javascript"> try { document.execCommand("BackgroundImageCache",false,true); } catch(e) {} </script> <![endif]-->  <script type="text/javascript"> blq.assetPath="http://static.bbc.co.uk/frameworks/barlesque/1.1.5/newnav/"; blqOnDomReady(function() { blq.addGoTrack('blq-content', {external:true});  blq.suggest_short = false; blq.addAutoSuggest(); }); </script> <!-- Identity head -->  
 
 
 
 
 
    
 
	
 
	<link rel="stylesheet" type="text/css" media="screen" href="/iplayer/r22008/style/style.css" /> 
	
 
	<!--[if LTE IE 7]>
		<link rel="stylesheet" type="text/css" media="screen" href="/iplayer/r22008/style/ie7_min.css" />
	
	<![endif]--> 
 
	<!--[if LTE IE 6]>
		<link rel="stylesheet" type="text/css" media="screen" href="/iplayer/r22008/style/ie6_min.css" />
	
	<![endif]--> 
 
	<script type="text/javascript"> 
		gloader.load(["glow","1.6.1","glow.anim","glow.dom","glow.embed","glow.events","glow.net","glow.tweens","glow.widgets.Overlay"]);
	</script> 
 
	<script type="text/javascript" src="/iplayer/r22008/script/js/global_en.js"></script> 
	<script type="text/javascript" src="/iplayer/r22008/script/js/playback.js"></script> 
	<script type="text/javascript" src="/iplayer/r22008/script/js/playback_download.js"></script> 
	<script type="text/javascript" src="/emp/embed_glow.js"></script> 
	<script type="text/javascript" src="/iplayer/r22008/script/common/sage_ntag_v003.js"></script> 
	
		<style type="text/css"> 
	@import '/guidance/style/pg_external.css?r164';
</style> 
<!--[if lte IE 7]>
<style type="text/css">
	@import '/guidance/style/pg_external_ie.css';
</style>
<![endif]--> 
<!--[if IE 6]>
<style type="text/css">
	@import '/guidance/style/pg_external_ie6.css';
</style>
<![endif]--> 
 
 
 
	
	<script type="text/javascript" src="/guidance/script/js/pg-gb.js?r164"></script> 
	
 
 
	<script type="text/javascript"> 
	<!--
		iplayer.sage.actiontrack.init(100);
		iplayer.config.episodeImgHost = "bbcimg.co.uk";
		iplayer.config.lastPlayedEnabled = 1;
		
		
		var i = new Image(1,1);
		i.src = "http://stats.bbc.co.uk/o.gif?~RS~s~RS~iPlayer~RS~t~RS~Web_progi~RS~i~RS~b00snb6w~RS~p~RS~0~RS~a~RS~v~RS~u~RS~/iplayer/_proxy_/episode/b00snb6w/The_Culture_Show_2010_2011_Episode_4/~RS~r~RS~(none)~RS~q~RS~~RS~z~RS~15~RS~";
 
		iplayer.sendDownloadStats = function() {
			var dwb = document.createElement("img");
			document.body.appendChild(dwb);
			dwb.width = 1;
			dwb.height = 1;
			dwb.src = "http://stats.bbc.co.uk/o.gif?~RS~s~RS~iplayer~RS~t~RS~Web_Downl~RS~i~RS~b00snb6w~RS~p~RS~0~RS~a~RS~v~RS~u~RS~/iplayer/_proxy_/episode/b00snb6w/The_Culture_Show_2010_2011_Episode_4/~RS~r~RS~(none)~RS~q~RS~~RS~z~RS~15~RS~";
		};
		
	//-->
	</script> 
 
	<!-- yes -->	<!-- yes --> 
 
</head> 
 
<body class="page-1column" id="body-episode"> 
	                <div id="blq-container" class="blq-lang-en-GB"> <div id="blq-pre-mast" lang="en-GB"> <!-- Pre mast -->   </div> <div id="blq-container-inner" lang="en-GB">  <div id="blq-acc" class="blq-rst blq-toolbar-dark"> <p id="blq-mast-home" class="blq-no-images"><a href="/" hreflang="en-GB" accesskey="1"> <span class="blq-home">British Broadcasting Corporation</span>  <img src="http://static.bbc.co.uk/frameworks/barlesque/1.1.5/newnav/img/blocks.png" alt="BBC" id="blq-blocks" width="107" height="32" />  <span class="blq-span">Home</span></a></p> <p class="blq-hide"><strong><a id="page-top">Accessibility links</a></strong></p> <ul id="blq-acc-links"> <li id="blq-acc-txt">   <a href="/cgi-bin/education/betsie/parser.pl">Text only</a>  </li> <li id="blq-acc-mobile"><a href="/mobile/">Mobiles</a></li> <li class="blq-hide"><a href="#blq-content" accesskey="2">Skip to content</a></li>  <li class="blq-hide"><a href="#blq-nav-links">Skip to bbc.co.uk navigation</a></li> <li class="blq-hide"><a href="#blq-search">Skip to bbc.co.uk search</a></li> <li id="blq-acc-help"><a href="/help/">Help</a></li> <li class="blq-hide"><a href="/accessibility/">Accessibility Help</a></li> <li class="blq-hide"><a href="/accessibility/accesskeys/keys.shtml" accesskey="0">Access keys help</a></li>   </ul> </div>   <div id="blq-main" class="blq-clearfix">     
<!-- start templates/navbar.tt --><div id="bip-header"> 
	<ul id="blq-local-nav"> 
		<li id="bip-logo"> 
			<a href="/iplayer/"> 
				<img src="/iplayer/img/iplayer_logo.gif" width="99" height="32" alt="BBC iPlayer" /> 
			</a> 
		</li> 
		<li id="home"> 
			<a href="/iplayer">Home</a> 
		</li> 
		<li id="tvchannels"> 
			<a href="/iplayer/tv">TV Channels</a> 
		</li> 
		<li id="radio"> 
			<a href="/iplayer/radio">Radio Stations</a> 
		</li> 
		<li id="categories"> 
			<a href="/iplayer/categories">Categories</a> 
		</li> 
		<li id="atoz"> 
			<a href="/iplayer/a">A to Z</a> 
		</li> 
	</ul> 
</div><!-- /bip-banner --> 
<!-- end templates/navbar.tt --><div id="bip-main"> 
		<div id="blq-content"><div id="bip-play-backdrop"> 
	<h1>The Culture Show - 2010/2011<span class="blq-hide"> - </span><span>Episode 4</span></h1> 
 
		<div id="bip-play-emp">					
													<div id="bip-play-error" class="jsdisabled"> 
								<p>To play or download The Culture Show: 2010/2011: Episode 4 you need to enable JavaScript.									<a href="http://iplayerhelp.external.bbc.co.uk/help/streaming_programmes/enable_java">How?</a> 
								</p> 
							</div>					<img src="http://node2.bbcimg.co.uk/iplayer/images/episode/b00snb6w_640_360.jpg" width="640" height="360" alt="The Culture Show: 2010/2011: Episode 4" id="bip-holding-image" /> 
		</div> 
 
		<div id="bip-play-head"> 
			<div class="title"><h2 class="ondemand">The Culture Show - 2010/2011<span class="blq-hide"> - </span><span>Episode 4</span></h2></div>		</div> 
	<div id="bip-play"> 
		<div class="detail"> 
			Andrew Graham-Dixon contemplates the past, present and future of British comic art; artist Grayson Perry looks at the dwindling craft of potting; while Tom Dyckhoff checks into hospital to find out if good design can actually improve our health. <br /> 
<br /> 
Plus an all male book group from Bolton checks out the Orange Prize shortlist, rising star Noel Clarke talks about his latest film and pictures from Platon - Brit photographer for the New Yorker.
			
 
			<dl><dt>Broadcast on:</dt><dd>BBC Two, 12:20am Friday 4th June 2010</dd> 
				<dt>Duration:</dt> 
				<dd>60 minutes</dd> 
 
				<dt>Available until:</dt> 
				<dd> 1:19am Friday 11th June 2010</dd> 
<dt>Categories:</dt><dd><ul>				<li class="9100005"><a href="/iplayer/categories/factual">Factual</a>, </li>				<li class="9200041"><a href="/iplayer/categories/factual/arts_culture_and_the_media">Arts, Culture &amp; the Media</a></li></ul></dd>			</dl> 
 
			<div class="sites">		<p class="website"><a href="http://www.bbc.co.uk/programmes/b006t6c5/microsite">Go to The Culture Show site</a></p>			</div> 
		</div> 
	</div> 
 
</div> 
 
 
<script type="text/javascript"> 
<!--
	iplayer.episode.setPid("b00snb6w","b00sn9vb");
	iplayer.episode.setTitle("The Culture Show: 2010/2011: Episode 4");
	iplayer.episode.setImages("http://node2.bbcimg.co.uk/iplayer/images/episode/b00snb6w_640_360.jpg","http://node2.bbcimg.co.uk/iplayer/images/episode/b00snb6w_832_468.jpg");
	iplayer.episode.setShortURL("bbc.co.uk/i/snb6w/");
	iplayer.episode.setVideoBitrateCeiling(2500,2500);
	iplayer.episode.setCountryIsUK("yes");
	iplayer.episode.setAvailVideoStreamTypes(1,1,1,0);
	iplayer.episode.setDownloadInfo(1,635,1,252,1,561);
	iplayer.episode.setWMVLicenceServer("1");
	iplayer.episode.setRecommendationSystem("choicestream");
	iplayer.episode.init();
	iplayer.episode.buildVideoPlayer();
//-->
</script> 
 
 
	
<div id="bip-play-recommendations" class="tab-content active-tab">	<h2>Recommendations</h2> 
	<div id="bip-play-recommendations-crsl" class="carousel"> 
		<div class="control prev"></div> 
			<div class="carousel-window"> 
				<ul class="carousel-content crsl"> 
<li class="episode pos_0 first-pane"><img src="http://node2.bbcimg.co.uk/iplayer/images/episode/b00sm0tw_178_100.jpg" width="178" height="100" alt="Mark Lawson Talks To: Vanessa Redgrave" />	<div class="feature video"> 
		<a class="play" href="/iplayer/episode/b00sm0tw/Mark_Lawson_Talks_To_Vanessa_Redgrave/?from=r"> 
			<span class="se-title">Mark Lawson Talks T...</span> 
		</a> 
	</div> 
	<div class="details pid_b00sm0tw"> 
		<span class="ep-title">Vanessa Redgrave</span> 
		<p>Mark Lawson talks to actress Vanessa Redgrave about her life and career. </p> 
	</div> 
</li> 
 
<li class="episode pos_1 first-pane"><img src="http://node1.bbcimg.co.uk/iplayer/images/episode/b00sl8bf_178_100.jpg" width="178" height="100" alt="Imagine: 1. The Stones in Exile" />	<div class="feature video"> 
		<a class="play" href="/iplayer/episode/b00sl8bf/Imagine_2010_11_The_Stones_in_Exile/?from=r"> 
			<span class="se-title">Imagine</span> 
		</a> 
	</div> 
	<div class="details pid_b00sl8bf"> 
		<span class="ep-title">1. The Stones in Exile</span> 
		<p>The story of the making of The Rolling Stones' acclaimed 1972 album Exile on Main S... </p> 
	</div> 
</li> 
 
<li class="episode pos_2 first-pane"><img src="http://node2.bbcimg.co.uk/iplayer/images/episode/b00sm18w_178_100.jpg" width="178" height="100" alt="Storyville: 20. The New Kings of Nigeria" />	<div class="feature video"> 
		<a class="play" href="/iplayer/episode/b00sm18w/Storyville_20092010_The_New_Kings_of_Nigeria/?from=r"> 
			<span class="se-title">Storyville</span> 
		</a> 
	</div> 
	<div class="details pid_b00sm18w"> 
		<span class="ep-title">20. The New Kings of Nige...</span> 
		<p>Film about elite young Nigerians returning to a burgeoning media world in Lagos. </p> 
	</div> 
</li> 
 
<li class="episode pos_3 first-pane"><img src="http://node2.bbcimg.co.uk/iplayer/images/episode/b00snk78_178_100.jpg" width="178" height="100" alt="I'm in a Rock 'n' Roll Band!: 5. The Band" />	<div class="feature video"> 
		<a class="play" href="/iplayer/episode/b00snk78/Im_in_a_Rock_n_Roll_Band!_The_Band/?from=r"> 
			<span class="se-title">I'm in a Rock 'n' R...</span> 
		</a> 
	</div> 
	<div class="details pid_b00snk78"> 
		<span class="ep-title">5. The Band</span> 
		<p>A no-holds barred romp through the classic shared journey that rock 'n' roll bands... </p> 
	</div> 
</li> 
 
<li class="episode pos_4 first-pane"><img src="http://node2.bbcimg.co.uk/iplayer/images/episode/b00slplb_178_100.jpg" width="178" height="100" alt="The Genius of Design: 4. Better Living Through Chemistry" />	<div class="feature video"> 
		<a class="play" href="/iplayer/episode/b00slplb/The_Genius_of_Design_Better_Living_Through_Chemistry/?from=r"> 
			<span class="se-title">The Genius of Desig...</span> 
		</a> 
	</div> 
	<div class="details pid_b00slplb"> 
		<span class="ep-title">4. Better Living Through...</span> 
		<p>The story of design enters the 50s and 60s, when a new material called plastic emer... </p> 
	</div> 
</li> 
 
<li class="episode pos_5"><img src="/iplayer/img/results/t.gif" id="node2:episode:b00psnt8_178_100" width="178" height="100" alt="Elvis by the Presleys Uncut: Elvis by the Presleys Uncut" />	<div class="feature video"> 
		<a class="play" href="/iplayer/episode/b00psnt8/Elvis_by_the_Presleys_Uncut/?from=r"> 
			<span class="se-title">Elvis by the Presle...</span> 
		</a> 
	</div> 
	<div class="details pid_b00psnt8"> 
		<span class="ep-title">Elvis by the Presleys Unc...</span> 
		<p>This is the story of Elvis's life and career told by those who knew him best, hi... <span class="abbr" title="Repeat"><abbr title="Repeat">(R)</abbr></span></p> 
	</div> 
</li> 
 
<li class="episode pos_6"><img src="/iplayer/img/results/t.gif" id="node2:episode:b00pqcg1_178_100" width="178" height="100" alt="Elvis in Las Vegas: Elvis in Las Vegas" />	<div class="feature video"> 
		<a class="play" href="/iplayer/episode/b00pqcg1/Elvis_in_Las_Vegas/?from=r"> 
			<span class="se-title">Elvis in Las Vegas</span> 
		</a> 
	</div> 
	<div class="details pid_b00pqcg1"> 
		<span class="ep-title">Elvis in Las Vegas</span> 
		<p>How Elvis Presley transformed Las Vegas in the 1970s and how Vegas helped to des... <span class="abbr" title="Repeat"><abbr title="Repeat">(R)</abbr></span></p> 
	</div> 
</li> 
 
<li class="episode pos_7"><img src="/iplayer/img/results/t.gif" id="node2:episode:b00gbjgm_178_100" width="178" height="100" alt="Blackadder Rides Again: Blackadder Rides Again" />	<div class="feature video"> 
		<a class="play" href="/iplayer/episode/b00gbjgm/Blackadder_Rides_Again/?from=r"> 
			<span class="se-title">Blackadder Rides Ag...</span> 
		</a> 
	</div> 
	<div class="details pid_b00gbjgm"> 
		<span class="ep-title">Blackadder Rides Again</span> 
		<p>Documentary marking 25 years of Blackadder, featuring interviews with the cast. <span class="abbr" title="Repeat"><abbr title="Repeat">(R)</abbr></span></p> 
	</div> 
</li> 
 
<li class="episode pos_8"><img src="/iplayer/img/results/t.gif" id="node2:episode:b00smm35_178_100" width="178" height="100" alt="Doctor Who Confidential: 9. What Goes on Tour ..." />	<div class="feature video"> 
		<a class="play" href="/iplayer/episode/b00smm35/Doctor_Who_Confidential_Series_5_What_Goes_on_Tour_.../?from=r"> 
			<span class="se-title">Doctor Who Confiden...</span> 
		</a> 
	</div> 
	<div class="details pid_b00smm35"> 
		<span class="ep-title">9. What Goes on Tour ...</span> 
		<p>Cameras follow the team as they travel the length of the UK to launch the new serie... </p> 
	</div> 
</li> 
 
<li class="episode pos_9"><img src="/iplayer/img/results/t.gif" id="node1:episode:b00sm1g0_178_100" width="178" height="100" alt="Rick Stein's Food of the Italian Opera: Rick Stein's Food of the Italian Opera" />	<div class="feature video"> 
		<a class="play" href="/iplayer/episode/b00sm1g0/Rick_Steins_Food_of_the_Italian_Opera/?from=r"> 
			<span class="se-title">Rick Stein's Food o...</span> 
		</a> 
	</div> 
	<div class="details pid_b00sm1g0"> 
		<span class="ep-title">Rick Stein's Food of the...</span> 
		<p>Rick Stein explores the part food has played in the creation of the Italian opera. </p> 
	</div> 
</li> 
 
<li class="episode pos_10"><img src="/iplayer/img/results/t.gif" id="node2:episode:b00sjllw_178_100" width="178" height="100" alt="Stephen Fry on Wagner: Stephen Fry on Wagner" />	<div class="feature video"> 
		<a class="play" href="/iplayer/episode/b00sjllw/Stephen_Fry_on_Wagner/?from=r"> 
			<span class="se-title">Stephen Fry on Wagn...</span> 
		</a> 
	</div> 
	<div class="details pid_b00sjllw"> 
		<span class="ep-title">Stephen Fry on Wagner</span> 
		<p>Stephen Fry explores his fascination for the controversial composer Richard Wagner. </p> 
	</div> 
</li> 
 
<li class="episode pos_11"><img src="/iplayer/img/results/t.gif" id="node2:episode:b00sm18t_178_100" width="178" height="100" alt="Opera Italia: 2. Viva Verdi" />	<div class="feature video"> 
		<a class="play" href="/iplayer/episode/b00sm18t/Opera_Italia_Viva_Verdi/?from=r"> 
			<span class="se-title">Opera Italia</span> 
		</a> 
	</div> 
	<div class="details pid_b00sm18t"> 
		<span class="ep-title">2. Viva Verdi</span> 
		<p>Antonio Pappano looks at the importance of Verdi to the history of Italian opera. </p> 
	</div> 
</li> 
 
<li class="episode pos_12"><img src="/iplayer/img/results/t.gif" id="node2:episode:b00s5kv1_178_100" width="178" height="100" alt="Great Movie Mistakes: Episode 13" />	<div class="feature video"> 
		<a class="play" href="/iplayer/episode/b00s5kv1/Great_Movie_Mistakes_Cutdowns_Episode_13/?from=r"> 
			<span class="se-title">Great Movie Mistake...</span> 
		</a> 
	</div> 
	<div class="details pid_b00s5kv1"> 
		<span class="ep-title">Episode 13</span> 
		<p>The cinematic blunders and gaffes that the film studios hoped they had got away wit... </p> 
	</div> 
</li> 
 
<li class="episode pos_13"><img src="/iplayer/img/results/t.gif" id="node2:episode:b00sjlxy_178_100" width="178" height="100" alt="Diva Diaries: Diva Diaries" />	<div class="feature video"> 
		<a class="play" href="/iplayer/episode/b00sjlxy/Diva_Diaries/?from=r"> 
			<span class="se-title">Diva Diaries</span> 
		</a> 
	</div> 
	<div class="details pid_b00sjlxy"> 
		<span class="ep-title">Diva Diaries</span> 
		<p>Soprano Danielle de Niese prepares for her role as Susanna in The Marriage of Figar... </p> 
	</div> 
</li> 
 
<li class="episode pos_14"><img src="/iplayer/img/results/t.gif" id="node2:episode:b00p90g8_178_100" width="178" height="100" alt="The Art of Russia: 1. Out of the Forest" />	<div class="feature video"> 
		<a class="play" href="/iplayer/episode/b00p90g8/The_Art_of_Russia_Out_of_the_Forest/?from=r"> 
			<span class="se-title">The Art of Russia</span> 
		</a> 
	</div> 
	<div class="details pid_b00p90g8"> 
		<span class="ep-title">1. Out of the Forest</span> 
		<p>Andrew Graham-Dixon explores the origins of the Russian religious icon. <span class="abbr" title="Repeat"><abbr title="Repeat">(R)</abbr></span></p> 
	</div> 
</li> 
 
<li class="episode pos_15"><img src="/iplayer/img/results/t.gif" id="node2:episode:b00sm1js_178_100" width="178" height="100" alt="What Makes a Great Tenor?: What Makes a Great Tenor?" />	<div class="feature video"> 
		<a class="play" href="/iplayer/episode/b00sm1js/What_Makes_a_Great_Tenor/?from=r"> 
			<span class="se-title">What Makes a Great...</span> 
		</a> 
	</div> 
	<div class="details pid_b00sm1js"> 
		<span class="ep-title">What Makes a Great Tenor?</span> 
		<p>Rolando Villazon takes us inside the world of the sexiest and riskiest of operatic... </p> 
	</div> 
</li> 
 
<li class="episode pos_16"><img src="/iplayer/img/results/t.gif" id="node2:episode:b0087f0s_178_100" width="178" height="100" alt="Top Gear: 4. Botswana Special" />	<div class="feature video"> 
		<a class="play" href="/iplayer/episode/b0087f0s/Top_Gear_Series_10_Botswana_Special/?from=r"> 
			<span class="se-title">Top Gear</span> 
		</a> 
	</div> 
	<div class="details pid_b0087f0s"> 
		<span class="ep-title">4. Botswana Special</span> 
		<p>Jeremy, Richard and James each drive second-hand cars across the wilds of Botswa... <span class="abbr" title="Repeat"><abbr title="Repeat">(R)</abbr></span></p> 
	</div> 
</li> 
 
<li class="episode pos_17"><img src="/iplayer/img/results/t.gif" id="node2:episode:b00sn5yz_178_100" width="178" height="100" alt="The Story of Science: Power, Proof and Passion: 6. Who Are We?" />	<div class="feature video"> 
		<a class="play" href="/iplayer/episode/b00sn5yz/The_Story_of_Science_Power_Proof_and_Passion_Who_Are_We/?from=r"> 
			<span class="se-title">The Story of Scienc...</span> 
		</a> 
	</div> 
	<div class="details pid_b00sn5yz"> 
		<span class="ep-title">6. Who Are We?</span> 
		<p>The sciences of brain anatomy and psychology have offered different visions of who... </p> 
	</div> 
</li> 
 
<li class="episode pos_18"><img src="/iplayer/img/results/t.gif" id="node2:episode:b00snkxs_178_100" width="178" height="100" alt="Richard Hammond's Engineering Connections: Guggenheim Bilbao" />	<div class="feature video"> 
		<a class="play" href="/iplayer/episode/b00snkxs/Richard_Hammonds_Engineering_Connections_Series_2_Guggenheim_Bilbao/?from=r"> 
			<span class="se-title">Richard Hammond's E...</span> 
		</a> 
	</div> 
	<div class="details pid_b00snkxs"> 
		<span class="ep-title">Guggenheim Bilbao</span> 
		<p>How a visionary architect transformed a decaying city with his futuristic building. </p> 
	</div> 
</li> 
				</ul> 
			</div> 
		<div class="control next"></div> 
	</div></div>		</div></div><div id="bip-footer"> 
			<p class="info"><a href="/iplayer/where_to_get_iplayer/">Access BBC iPlayer on your favourite device</a></p> 
		<ul> 
			<li><a href="http://iplayerhelp.external.bbc.co.uk/help/about_iplayer">About BBC iPlayer</a></li> 
			<li><a href="http://iplayerhelp.external.bbc.co.uk/help/about_iplayer/termscon">BBC iPlayer Terms &amp; Conditions</a></li>			<li class="help"><span class="icon"><a href="http://iplayerhelp.external.bbc.co.uk/help/">Help</a></span></li> 
		</ul></div> 
	
	                </div>   <div id="blq-mast" class="blq-rst blq-toolbar-dark blq-new-nav" lang="en-GB"> <!-- Identity status -->  <form method="get" action="http://search.bbc.co.uk/search" accept-charset="utf-8"> <p>  <input type="hidden" name="go" value="toolbar" />  <input type="hidden" name="uri" value="/iplayer/episode/b00snb6w/The_Culture_Show_2010_2011_Episode_4/" />    <input type="hidden" name="scope" value="iplayer" />  <label for="blq-search" class="blq-hide">Search term:</label> <input id="blq-search" type="text" name="q" value="" maxlength="128" accesskey="4" /> <input id="blq-search-btn" type="submit" value="Search" /> </p> </form>  <h2 class="blq-hide">bbc.co.uk navigation</h2> <ul id="blq-nav-main">     <li id="blq-nav-n"><a href="http://news.bbc.co.uk/news/" hreflang="en-GB">News</a></li> <li id="blq-nav-s"><a href="http://news.bbc.co.uk/sport/" hreflang="en-GB">Sport</a></li> <li id="blq-nav-w"><a href="http://news.bbc.co.uk/weather/" hreflang="en-GB">Weather</a></li>  <li id="blq-nav-i">  <a href="/iplayer/">iPlayer</a>  </li>  <li id="blq-nav-t"><a href="/tv/" hreflang="en-GB">TV</a></li>  <li id="blq-nav-r"><a href="/radio/" hreflang="en-GB">Radio</a></li> <li id="blq-nav-m"><a href="#blq-nav">More&hellip;</a></li>  </ul> </div>  <div id="blq-nav" class="blq-magenta blq-rst"> <div id="blq-nav-links" class="blq-clearfix" lang="en-GB"> <div id="blq-nav-links-inner">   <h3 class="blq-hide">A to F</h3> <ol class="blq-nav-sub blq-first"> <li><a href="/cbbc/">CBBC</a></li> <li><a href="/cbeebies/">CBeebies</a></li> <li><a href="/food/">Food</a></li> </ol> <h3 class="blq-hide">H to Le</h3> <ol class="blq-nav-sub"> <li><a href="/health/">Health</a></li> <li><a href="/history/">History</a></li> <li><a href="/learning/">Learning</a></li> </ol> <h3 class="blq-hide">Lo to Z</h3> <ol class="blq-nav-sub blq-last"> <li><a href="/local/">Nations &amp; Local</a></li> <li><a href="/music/">Music</a></li> <li><a href="/sn/">Science &amp; Nature</a></li> </ol>  </div> <div id="blq-nav-foot"><div>  <h3 class="blq-hide">Popular links</h3> <ul id="blq-pop"> <!--   --> <li><a href="http://www.bbc.co.uk/solarsystem">Solar System</a></li> <li><a href="http://www.bbc.co.uk/ahistoryoftheworld/">100 Objects</a></li> 
 </ul>  <p id="blq-az"><a href="/a-z/" accesskey="3">Full A-Z<span class="blq-hide"> of BBC sites</span></a></p> <p class="blq-hide"><a href="#blq-nav-links-inner">Back to start of navigation</a></p></div> </div> </div> </div> <div id="blq-foot" lang="en-GB" class="blq-rst blq-clearfix blq-foot-black"> <div id="blq-footlinks">  <h2 class="blq-hide">Site links</h2> <ul id="blq-sitelinks"> <li><a href="/guidance">Parental Guidance</a></li>    </ul>  <h2 class="blq-hide">BBC links</h2> <ul id="blq-bbclinks"> <li><a href="/aboutthebbc/">About the BBC</a></li> <li><a href="/help/">BBC Help</a></li> <li><a href="/feedback/">Contact Us</a></li> <li><a href="/accessibility/">Accessibility Help</a></li> <li><a href="/terms/">Terms of Use</a></li>  <li><a href="/jobs/">Jobs</a></li>  <li><a href="/privacy/">Privacy &amp; Cookies</a></li>  </ul> </div>  <p id="blq-copy"><img src="http://static.bbc.co.uk/frameworks/barlesque/1.1.5/newnav/img/footer_blocks_black.gif" width="68" height="21" alt="BBC" /> &copy; MMX</p> <p id="blq-disclaim"><a href="/help/web/links/">The BBC is not responsible for the content of external internet sites.</a></p> <div id="blq-obit"><p><strong>This page is best viewed in an up-to-date web browser with style sheets (CSS) enabled. While you will be able to view the content of this page in your current browser, you will not be able to get the full visual experience. Please consider upgrading your browser software or enabling style sheets (CSS) if you are able to do so.</strong></p></div> </div> </div>  </div>     
 
 
	
		
	
		
	
<script type="text/javascript"> 
<!--
sageTrack_detail("775","d005","","avl:0,ver:1,cgr:1,ch:bbc_two,ei:b00snb6w,et:Episode%204,g1:9100005,me:0,pi:b006t6c5,pt:The%20Culture%20Show,st:The%20Culture%20Show%3A%202010%2F2011,ste:iplayer,ty:episode,lab:" + (iplayer.user.getLabsEnabled() ? 1 : 0) + ",pg:" + iplayer.user.getPGmode() + ",uu:" + iplayer.user.getBBCuid() + ",sz:" + iplayer.user.getEmpSizeInfo().sz + ",psz:" + iplayer.user.getEmpSizeInfo().psz + ",tst:" + iplayer.episode.getOffsetTimeInSeconds());
// -->
</script> 
 
<noscript> 
	<div><img src="http://su.sageanalyst.net/NS?ci=775&amp;di=d003&amp;pg=&amp;ai=hn:bbc.co.uk,uri:/iplayer" width="1" height="1" alt="" /></div> 
</noscript> 
	
 
	
</body> 
</html> 

```

---

### Post by lovinglinux on 2010-06-04
> **goseph said:**
> Does this help? :) This is page source when a random show is playing, for the iPlayer

Yes, it helps. Thanks.

---

