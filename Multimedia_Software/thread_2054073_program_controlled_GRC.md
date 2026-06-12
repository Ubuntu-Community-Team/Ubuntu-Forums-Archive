---
title: "program controlled GRC"
date: 2012-09-06
forum: Multimedia Software
---

### Post by xzero1 on 2012-09-06
For those not familiar with **gnuradio** and **grc** here is a helpful link:    [http://superkuh.com/gnuradio.html#simple]("http://superkuh.com/gnuradio.html#simple")

Using a simple "hack", some of the grc flow graph can be program controlled by adding your own code. The basic idea is to use a
function probe in your flow graph. This sets up an independent thread which one can use to interact with the rest of the flow
graph with one's own code. Of course, one could create their own threads as required. If only one could access the actual arrays in this way, but I digress. 

As an example, I have created a FM radio with seek capabilities. See the attached "Sradio.grc.zip" file.

To add the seek function, one must add or replace code in the grc generated python file. Here I replace the _probe_probe()
with my seek code:
```
		def scan(scanmode):
		        if scanmode == 1: return
		        self.set_squelchThreshold(10) # mute while scanning
			step = 0.2 if scanmode == 2 else -0.2
			f = self.f + step
			if f > 108: f = 87.5
			if f < 87.5: f = 108.1 # must be odd freq
			self.set_f(f)
		        
		# find greatest level in scanmode direction (assumes positive slope)
		def scantune(scanmode,val):
		   print "\nscantune %4.1f %f" % (self.f,val)
		   self.set_variable_qtgui_chooser_0(1)
		   step = 0.2 if scanmode == 2 else -0.2
		   while True:	   		
		   	f=self.f + step
		   	self.set_f(f)
		   	time.sleep(0.5)
		   	newval = self.avgmag2.level() 
		   	print "%4.2f %f %4.2f %f" % (f-step,val,f,newval)
		   	if (newval <= val + self.epsilon): break
		   	val = newval
                   f=self.f - step
		   self.set_f(f)
		
		def _probe_probe():
			while True:
				val = self.avgmag2.level()
				if (val > scanThreshold) and (scanmode <> 1) and (oldval < val):
				   scantune(scanmode,val)
				   scanmode = 1
				else:
				   self.set_squelchThreshold(squelchThreshold) # unmute
				   scanmode = self.get_variable_qtgui_chooser_0()
				   scan(scanmode)
				   oldval = val
				try: self.set_probe(val)
				except AttributeError, e: pass
				time.sleep(1.0/(5))

```

Don't forget indentation is important in python!


Finally, *move* the thread start call "_probe_thread.start()" to the end of the initialization code so everything is properly initialized.

Here is the final code Sradio.py:
```
#!/usr/bin/env python
##################################################
# Gnuradio Python Flow Graph
# Title: Sradio
# Author: Keith Nuesslein
# Description: Sradio 1.01 FM radio with seek tuning
# Generated: Fri Sep  7 10:17:42 2012
##################################################

from PyQt4 import Qt
from gnuradio import audio
from gnuradio import blks2
from gnuradio import eng_notation
from gnuradio import gr
from gnuradio.eng_option import eng_option
from gnuradio.gr import firdes
from optparse import OptionParser
import PyQt4.Qwt5 as Qwt
import baz
import sys
import threading
import time

class Sradio(gr.top_block, Qt.QWidget):

	def __init__(self, squelchThreshold=-60, deemphasis=75e-6, defaultStation=96.7, lpfCutoff=100000, magAlpha=0.001, sdrFreqCorr=82, srate=1.920e6, rfGain=1, epsilon=.01, scanThreshold=0.3):
		gr.top_block.__init__(self, "Sradio")
		Qt.QWidget.__init__(self)
		self.setWindowTitle("Sradio")
		self.setWindowIcon(Qt.QIcon.fromTheme('gnuradio-grc'))
		self.top_scroll_layout = Qt.QVBoxLayout()
		self.setLayout(self.top_scroll_layout)
		self.top_scroll = Qt.QScrollArea()
		self.top_scroll.setFrameStyle(Qt.QFrame.NoFrame)
		self.top_scroll_layout.addWidget(self.top_scroll)
		self.top_scroll.setWidgetResizable(True)
		self.top_widget = Qt.QWidget()
		self.top_scroll.setWidget(self.top_widget)
		self.top_layout = Qt.QVBoxLayout(self.top_widget)
		self.top_grid_layout = Qt.QGridLayout()
		self.top_layout.addLayout(self.top_grid_layout)


		##################################################
		# Parameters
		##################################################
		self.squelchThreshold = squelchThreshold
		self.deemphasis = deemphasis
		self.defaultStation = defaultStation
		self.lpfCutoff = lpfCutoff
		self.magAlpha = magAlpha
		self.sdrFreqCorr = sdrFreqCorr
		self.srate = srate
		self.rfGain = rfGain
		self.epsilon = epsilon
		self.scanThreshold = scanThreshold

		##################################################
		# Variables
		##################################################
		self.probe = probe = 0
		self.f = f = defaultStation
		self.vol = vol = 1
		self.variable_qtgui_label_0 = variable_qtgui_label_0 = "%7.3f %23s%6.1f Mhz" % (probe," ",f) 
		self.variable_qtgui_chooser_0 = variable_qtgui_chooser_0 = 1
		self.samp_rate = samp_rate = srate
		self.dec = dec = 8

		##################################################
		# Blocks
		##################################################
		self._vol_layout = Qt.QVBoxLayout()
		self._vol_label = Qt.QLabel("Volume")
		self._vol_slider = Qwt.QwtSlider(None, Qt.Qt.Horizontal, Qwt.QwtSlider.BottomScale, Qwt.QwtSlider.BgSlot)
		self._vol_slider.setRange(0, 10, .5)
		self._vol_slider.setValue(self.vol)
		self._vol_slider.setMinimumWidth(200)
		self._vol_slider.valueChanged.connect(self.set_vol)
		self._vol_label.setAlignment(Qt.Qt.AlignBottom | Qt.Qt.AlignHCenter)
		self._vol_layout.addWidget(self._vol_label)
		self._vol_layout.addWidget(self._vol_slider)
		self.top_grid_layout.addLayout(self._vol_layout, 2,10)
		self._f_layout = Qt.QVBoxLayout()
		self._f_label = Qt.QLabel("FM Tuner")
		self._f_slider = Qwt.QwtSlider(None, Qt.Qt.Horizontal, Qwt.QwtSlider.BottomScale, Qwt.QwtSlider.BgSlot)
		self._f_slider.setRange(87.5, 108.1, .2)
		self._f_slider.setValue(self.f)
		self._f_slider.setMinimumWidth(200)
		self._f_slider.valueChanged.connect(self.set_f)
		self._f_label.setAlignment(Qt.Qt.AlignBottom | Qt.Qt.AlignHCenter)
		self._f_layout.addWidget(self._f_label)
		self._f_layout.addWidget(self._f_slider)
		self.top_grid_layout.addLayout(self._f_layout, 0,1,1,10)
		self.avgmag2 = gr.probe_avg_mag_sqrd_c(squelchThreshold, magAlpha)
		self._variable_qtgui_label_0_tool_bar = Qt.QToolBar(self)
		self._variable_qtgui_label_0_tool_bar.addWidget(Qt.QLabel("Signal"+": "))
		self._variable_qtgui_label_0_label = Qt.QLabel(str(self.variable_qtgui_label_0))
		self._variable_qtgui_label_0_tool_bar.addWidget(self._variable_qtgui_label_0_label)
		self.top_grid_layout.addWidget(self._variable_qtgui_label_0_tool_bar, 3,1,1,10)
		self._variable_qtgui_chooser_0_options = (0, 1, 2, )
		self._variable_qtgui_chooser_0_labels = ("DOWN", "STOP", "UP", )
		self._variable_qtgui_chooser_0_group_box = Qt.QGroupBox("Seekmode")
		self._variable_qtgui_chooser_0_box = Qt.QHBoxLayout()
		self._variable_qtgui_chooser_0_button_group = Qt.QButtonGroup()
		self._variable_qtgui_chooser_0_group_box.setLayout(self._variable_qtgui_chooser_0_box)
		for i, label in enumerate(self._variable_qtgui_chooser_0_labels):
			radio_button = Qt.QRadioButton(label)
			self._variable_qtgui_chooser_0_box.addWidget(radio_button)
			self._variable_qtgui_chooser_0_button_group.addButton(radio_button, i)
		self._variable_qtgui_chooser_0_callback = lambda i: self._variable_qtgui_chooser_0_button_group.button(self._variable_qtgui_chooser_0_options.index(i)).setChecked(True)
		self._variable_qtgui_chooser_0_callback(self.variable_qtgui_chooser_0)
		self._variable_qtgui_chooser_0_button_group.buttonClicked[int].connect(
			lambda i: self.set_variable_qtgui_chooser_0(self._variable_qtgui_chooser_0_options[i]))
		self.top_grid_layout.addWidget(self._variable_qtgui_chooser_0_group_box, 2,1)
		self.rtl2832_source_0 = baz.rtl_source_c(defer_creation=True, output_size=gr.sizeof_gr_complex)
		self.rtl2832_source_0.set_verbose(True)
		self.rtl2832_source_0.set_vid(0x0)
		self.rtl2832_source_0.set_pid(0x0)
		self.rtl2832_source_0.set_tuner_name("e4k")
		self.rtl2832_source_0.set_default_timeout(0)
		self.rtl2832_source_0.set_use_buffer(True)
		self.rtl2832_source_0.set_fir_coefficients(([]))
		
		self.rtl2832_source_0.set_read_length(0)
		
		
		
		
		if self.rtl2832_source_0.create() == False: raise Exception("Failed to create RTL2832 Source: rtl2832_source_0")
		
		
		self.rtl2832_source_0.set_sample_rate(samp_rate)
		
		self.rtl2832_source_0.set_frequency(f*1e6)
		
		
		
		self.rtl2832_source_0.set_auto_gain_mode(False)
		self.rtl2832_source_0.set_relative_gain(True)
		self.rtl2832_source_0.set_gain(rfGain)
		  

		def scan(scanmode):
		        if scanmode == 1: return
		        self.set_squelchThreshold(10) # mute while scanning
			step = 0.2 if scanmode == 2 else -0.2
			f = self.f + step
			if f > 108: f = 87.5
			if f < 87.5: f = 108.1 # must be odd freq
			self.set_f(f)
		        
		# find greatest level in scanmode direction (assumes positive slope)
		def scantune(scanmode,val):
		   print "\nscantune %4.1f %f" % (self.f,val)
		   self.set_variable_qtgui_chooser_0(1)
		   step = 0.2 if scanmode == 2 else -0.2
		   while True:	   		
		   	f=self.f + step
		   	self.set_f(f)
		   	time.sleep(0.5)
		   	newval = self.avgmag2.level() 
		   	print "%4.2f %f %4.2f %f" % (f-step,val,f,newval)
		   	if (newval <= val + self.epsilon): break
		   	val = newval
                   f=self.f - step
		   self.set_f(f)
		
		def _probe_probe():
			while True:
				val = self.avgmag2.level()
				if (val > scanThreshold) and (scanmode <> 1) and (oldval < val):
				   scantune(scanmode,val)
				   scanmode = 1
				else:
				   self.set_squelchThreshold(squelchThreshold) # unmute
				   scanmode = self.get_variable_qtgui_chooser_0()
				   scan(scanmode)
				   oldval = val
				try: self.set_probe(val)
				except AttributeError, e: pass
				time.sleep(1.0/(5))
				
		_probe_thread = threading.Thread(target=_probe_probe)
		_probe_thread.daemon = True
		
		self.low_pass_filter_1 = gr.fir_filter_fff(5, firdes.low_pass(
			vol*50, samp_rate/dec, 15000, 1000, firdes.WIN_HAMMING, 6.76))
		self.low_pass_filter_0 = gr.fir_filter_ccf(dec, firdes.low_pass(
			4, samp_rate, lpfCutoff, 8000, firdes.WIN_HAMMING, 6.76))
		self.gr_simple_squelch_cc_0 = gr.simple_squelch_cc(squelchThreshold, magAlpha)
		self.blks2_wfm_rcv_0 = blks2.wfm_rcv(
			quad_rate=samp_rate/dec,
			audio_decimation=1,
		)
		self.blks2_fm_deemph_0 = blks2.fm_deemph(fs=samp_rate/dec, tau=deemphasis)
		self.audio_sink_0 = audio.sink(48000, "pulse", True)

		##################################################
		# Connections
		##################################################
		self.connect((self.low_pass_filter_0, 0), (self.avgmag2, 0))
		self.connect((self.gr_simple_squelch_cc_0, 0), (self.blks2_wfm_rcv_0, 0))
		self.connect((self.blks2_wfm_rcv_0, 0), (self.blks2_fm_deemph_0, 0))
		self.connect((self.low_pass_filter_0, 0), (self.gr_simple_squelch_cc_0, 0))
		self.connect((self.low_pass_filter_1, 0), (self.audio_sink_0, 0))
		self.connect((self.blks2_fm_deemph_0, 0), (self.low_pass_filter_1, 0))
		self.connect((self.rtl2832_source_0, 0), (self.low_pass_filter_0, 0))
		_probe_thread.start()

	def get_squelchThreshold(self):
		return self.squelchThreshold

	def set_squelchThreshold(self, squelchThreshold):
		self.squelchThreshold = squelchThreshold
		self.avgmag2.set_threshold(self.squelchThreshold)
		self.gr_simple_squelch_cc_0.set_threshold(self.squelchThreshold)

	def get_deemphasis(self):
		return self.deemphasis

	def set_deemphasis(self, deemphasis):
		self.deemphasis = deemphasis

	def get_defaultStation(self):
		return self.defaultStation

	def set_defaultStation(self, defaultStation):
		self.defaultStation = defaultStation
		self.set_f(self.defaultStation)

	def get_lpfCutoff(self):
		return self.lpfCutoff

	def set_lpfCutoff(self, lpfCutoff):
		self.lpfCutoff = lpfCutoff
		self.low_pass_filter_0.set_taps(firdes.low_pass(4, self.samp_rate, self.lpfCutoff, 8000, firdes.WIN_HAMMING, 6.76))

	def get_magAlpha(self):
		return self.magAlpha

	def set_magAlpha(self, magAlpha):
		self.magAlpha = magAlpha
		self.avgmag2.set_alpha(self.magAlpha)
		self.gr_simple_squelch_cc_0.set_alpha(self.magAlpha)

	def get_sdrFreqCorr(self):
		return self.sdrFreqCorr

	def set_sdrFreqCorr(self, sdrFreqCorr):
		self.sdrFreqCorr = sdrFreqCorr

	def get_srate(self):
		return self.srate

	def set_srate(self, srate):
		self.srate = srate
		self.set_samp_rate(self.srate)

	def get_rfGain(self):
		return self.rfGain

	def set_rfGain(self, rfGain):
		self.rfGain = rfGain
		self.rtl2832_source_0.set_gain(self.rfGain)

	def get_epsilon(self):
		return self.epsilon

	def set_epsilon(self, epsilon):
		self.epsilon = epsilon

	def get_scanThreshold(self):
		return self.scanThreshold

	def set_scanThreshold(self, scanThreshold):
		self.scanThreshold = scanThreshold

	def get_probe(self):
		return self.probe

	def set_probe(self, probe):
		self.probe = probe
		self.set_variable_qtgui_label_0("%7.3f %23s%6.1f Mhz" % (self.probe," ",self.f) )

	def get_f(self):
		return self.f

	def set_f(self, f):
		self.f = f
		self.set_variable_qtgui_label_0("%7.3f %23s%6.1f Mhz" % (self.probe," ",self.f) )
		self._f_slider.setValue(self.f)
		self.rtl2832_source_0.set_frequency(self.f*1e6)

	def get_vol(self):
		return self.vol

	def set_vol(self, vol):
		self.vol = vol
		self._vol_slider.setValue(self.vol)
		self.low_pass_filter_1.set_taps(firdes.low_pass(self.vol*50, self.samp_rate/self.dec, 15000, 1000, firdes.WIN_HAMMING, 6.76))

	def get_variable_qtgui_label_0(self):
		return self.variable_qtgui_label_0

	def set_variable_qtgui_label_0(self, variable_qtgui_label_0):
		self.variable_qtgui_label_0 = variable_qtgui_label_0
		self._variable_qtgui_label_0_label.setText(str(self.variable_qtgui_label_0))

	def get_variable_qtgui_chooser_0(self):
		return self.variable_qtgui_chooser_0

	def set_variable_qtgui_chooser_0(self, variable_qtgui_chooser_0):
		self.variable_qtgui_chooser_0 = variable_qtgui_chooser_0
		self._variable_qtgui_chooser_0_callback(self.variable_qtgui_chooser_0)

	def get_samp_rate(self):
		return self.samp_rate

	def set_samp_rate(self, samp_rate):
		self.samp_rate = samp_rate
		self.low_pass_filter_0.set_taps(firdes.low_pass(4, self.samp_rate, self.lpfCutoff, 8000, firdes.WIN_HAMMING, 6.76))
		self.low_pass_filter_1.set_taps(firdes.low_pass(self.vol*50, self.samp_rate/self.dec, 15000, 1000, firdes.WIN_HAMMING, 6.76))
		self.rtl2832_source_0.set_sample_rate(self.samp_rate)

	def get_dec(self):
		return self.dec

	def set_dec(self, dec):
		self.dec = dec
		self.low_pass_filter_1.set_taps(firdes.low_pass(self.vol*50, self.samp_rate/self.dec, 15000, 1000, firdes.WIN_HAMMING, 6.76))

if __name__ == '__main__':
	parser = OptionParser(option_class=eng_option, usage="%prog: [options]")
	parser.add_option("-t", "--squelchThreshold", dest="squelchThreshold", type="intx", default=-60,
		help="Set squelchThreshold [default=%default]")
	parser.add_option("-e", "--deemphasis", dest="deemphasis", type="eng_float", default=eng_notation.num_to_str(75e-6),
		help="Set deemphasis [default=%default]")
	parser.add_option("-d", "--defaultStation", dest="defaultStation", type="eng_float", default=eng_notation.num_to_str(96.7),
		help="Set (Mhz) [default=%default]")
	parser.add_option("-l", "--lpfCutoff", dest="lpfCutoff", type="long", default=100000,
		help="Set rf lowpass filter [default=%default]")
	parser.add_option("-m", "--magAlpha", dest="magAlpha", type="eng_float", default=eng_notation.num_to_str(0.001),
		help="Set signal mag alpha [default=%default]")
	parser.add_option("-c", "--sdrFreqCorr", dest="sdrFreqCorr", type="intx", default=82,
		help="Set sdrFreqCorr [default=%default]")
	parser.add_option("-r", "--srate", dest="srate", type="eng_float", default=eng_notation.num_to_str(1.920e6),
		help="Set srate [default=%default]")
	parser.add_option("-g", "--rfGain", dest="rfGain", type="eng_float", default=eng_notation.num_to_str(1),
		help="Set rfGain [default=%default]")
	parser.add_option("-p", "--epsilon", dest="epsilon", type="eng_float", default=eng_notation.num_to_str(.01),
		help="Set min diff [default=%default]")
	parser.add_option("-s", "--scanThreshold", dest="scanThreshold", type="eng_float", default=eng_notation.num_to_str(0.3),
		help="Set scan signal detect threshold [default=%default]")
	(options, args) = parser.parse_args()
	qapp = Qt.QApplication(sys.argv)
	tb = Sradio(squelchThreshold=options.squelchThreshold, deemphasis=options.deemphasis, defaultStation=options.defaultStation, lpfCutoff=options.lpfCutoff, magAlpha=options.magAlpha, sdrFreqCorr=options.sdrFreqCorr, srate=options.srate, rfGain=options.rfGain, epsilon=options.epsilon, scanThreshold=options.scanThreshold)
	tb.start()
	tb.show()
	qapp.exec_()
	tb.stop()


```

The Sradio.py application depends on signal strength comparisons so disabling agc is highly desirable, however, in my case the 
RTL2832 source block will crash if the frequency is changed too quickly. There may also be a need for tweaking some other parameters depending on one's setup.

EDIT: Choosing the RTL2832 source with the Osmo E4000 device seems to prevents crashing. I will revise the code and post an update at a later time.
EDIT: I have updated the zip file with the new Osmo E4000 source modifications and added Sradio.py. Use Sradio.py -h for additional options. The GRC file will need to be modified for other than E4000 sources.

---

### Post by xzero1 on 2012-10-12
SRADIO 2.0: A GNU-RADIO FM STEREO PLL TUNER APPLICATION

[ATTACH]225455[/ATTACH]

The GRC file

The GRC file generates a stereo FM tuner utilizing the QT UI. Consider it a framework for the full tuner implementation. Expanding on the method from Sradio 1.0 (see the post above), the GRC generated python code is modified. Although the compiled python file will execute, it is designed to be modified for full functionality. The full implementation is provided in the attachments.

The tuner uses a PLL for the stereo carrier regeneration. The stereo pilot is not detected, rather stereo will be decoded when the PLL is sufficiently locked. The audio at 48k is designed to be an integer factor of the master sample rate of 960000 but this could be changed without too much difficulty. The source specifically uses the RTL2832 block with normalized gain settings and the Osmocom E4000 tuner. It will need to be modified appropriately for other tuners. Hopefully, I have made it relatively easy to do so.

I began with the wfm_rcv_pll block. I learned much from the helpful comments in the python file and after a few substitutions and tweaking, finally had good sound. The final decoding scheme was inspired by Alfredo Vega Irizarry's research*. The basic change was dropping the DSB filter and using positive frequencies.


The Sradio application

This is version 2.0 of Sradio. While remaining compact it adds stereo, signal level meter, offset tuning, favorite list tuning, a config file (for favorites), optional audio scope view, L/R audio meters and various related program parameters. Most options are self-explanatory. The options "scanThreshold" and "epsilon" are used for tuning the automatic station search function. Option "scopeoffset" is a preference that seperates the left and right traces in the scope view. Option "LmRM" is interesting, it controls the stereo carrier level, which relates to the amount of "center" and seperation in the stereo image. Greater values may give more interesting results but adds noise, lesser values reduce noise as well as the stereo effect. Note that the "favorites" option is meant to temporarily override values in your config file. Once the config file is created, it must be edited to change its values. It is possible to use other decimation levels of 1,2,4 (try say 3 for fun) but the corresponding st_High (-S) and st_Low (-s) thresholds will probably need tweaking for proper stereo detection.
 
Installation and Executing

I have provided a sed script which adds the features mentioned to the python code generated from the GRC compilation. Of course, some changes in the GRC file might require change(s) to the sed script. To create
the Sradio.py application use the following command line:

sed -f Sradio_creator.cmd Sradio_GRC.py > Sradio.py

Use the command line "./Sradio.py" to run and the -h option for option help. The first run of Sradio.py creates an "Sradio.conf" file in ~/.config/GRC. Please enter a comma seperated ordered list of your favorite stations when prompted (no quotes).
 
 
Known bugs: 

At this time the "scope" and "meter" options have been known to cause problems. This is more likely a bug in multitasking of the GRC UI implementation since it can occur before any program modifications are made to the GRC file and tends to freeze portions of the UI. The "meter" option seems to have the most issues. In most cases, these bugs do not interfere with other program functionality. On occasion, I also have gotten segmentation faults.
 

* See [http://www.dtic.mil/dtic/tr/fulltext/u2/a412239.pdf](http://www.dtic.mil/dtic/tr/fulltext/u2/a412239.pdf)

Other useful links:

[http://www.radioworld.com/article/a-method-to-improve-conventional-fm-stereo/4000](http://www.radioworld.com/article/a-method-to-improve-conventional-fm-stereo/4000)
[http://www1.verigy.com/cntrprod/groups/public/documents/webcontent/topic41_fmstereo.pdf](http://www1.verigy.com/cntrprod/groups/public/documents/webcontent/topic41_fmstereo.pdf)

For more than you ever want to know about why FM can sound so crappy (and why it will probably get worse):

[http://dspace.mit.edu/bitstream/handle/1721.1/4212/RLE-TR-540-20137017.pdf?sequence=1](http://dspace.mit.edu/bitstream/handle/1721.1/4212/RLE-TR-540-20137017.pdf?sequence=1)

---

### Post by kb3lms on 2013-03-09
Very nice!  I'm pursing the idea of a P25 Phase II scanner.  Some great ideas here!

---

