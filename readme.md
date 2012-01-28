# Page Scroll jQuery Plugin
Yet another and in small ways different page scroll plugin.



## Features

**Setting the scroll speed OR the total duration.** Or set the speed with a maximum duration.
Personally I find a constant speed a better experience for short scrolls, but scrolling a long page would take too long. With a max duration set, scrolling is always constant up to a given length.

**Callback functions beforeScroll and afterScroll.** Both functions get the scroll options object passed that can be changed "on the fly".
The beforeScroll function also acts as a delegate: pass 'false' to stop scrolling.

Both callback functions can be **called after an optional delay.** For instance to scroll up to tab pane buttons, wait a little, and switch to a different tab.

Of course the plugin supports expected features: target, offset, easing.



## Usage


Quick and easy - add page scrolling to all links on the page:

        $("a").pageScroll();

Or to target anchor links only:

        $("a[href*='#']").pageScroll();
		
Or pass options:

        $("a").pageScroll({
            duration: 3000
        });
		
		
Conditionally stop scrolling:
	
        $('a').pageScroll({
            beforeScroll: function(opts) {
                var stop = confirm("Stop scrolling?");
                if (stop) {
                    return false;
                } else {
                    return true;
                }
            }
        });

Change the scroll object:
	
        $('a').pageScroll({
            beforeScroll: function(opts) {
                alert("before scroll; duration=" + opts.duration);
                // speed up
                opts.duration = 100;
            },
            afterScroll: function(opts) {
                alert("after scroll; duration=" + opts.duration);
            },
        });



## Options
* `speed`: pixels per second; calculates the duration
* `maxDuration`: (only used with `speed`) maximum scroll duration in milliseconds
* `offset`: pixels
* `duration`: explicitly set scroll duration in milliseconds; 0 means immediate (no scrolling easing); overrides `speed`
* `easing`: easing name, like 'swing' (default) (use jquery.easing for more easing possibilities)
* `beforeScroll`: function called when scrolling is complete; the function is called with the "scroll options" object as parameter; return false to stop scrolling.
* `beforeScrollDelay`: milliseconds to wait before scrolling
* `afterScroll`: function called when scrolling is complete; the function is called with the "scroll options" object as parameter
* `afterScrollDelay`: milliseconds to wait before calling afterScroll; default 0
* `scroller`: jQuery selector to scroll; default 'body'
* `target`: jQuery element to scroll to; default not set

				
## Demo
See at http://arthurclemens.github.com/jquery-page-scroll-plugin/


## License
The MIT License

Copyright (c) 2012 Arthur Clemens, arthur@visiblearea.com

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.