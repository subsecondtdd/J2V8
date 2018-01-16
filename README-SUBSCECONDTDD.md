# Subsecond TDD

J2V8's Node.js library can be used to run *fast* full-stack acceptance tests on 
the JVM, with everything in the same process:

* Browser/DOM app in JavaScript (React, Vue.js, whatever)
* Server app (Java, Clojure, whatever)

With adequate design of both the browser app and the server app, HTTP and other
forms of I/O can be removed, further improving the speed of tests.

This repo is a fork based of J2V8 with Node 8.2.1 support by [@matiwinnetou](https://github.com/eclipsesource/J2V8/compare/master...matiwinnetou:nodejs8),
based on [eclipsesource/J2V8#334](https://github.com/eclipsesource/J2V8/issues/334). 
We need Node 8 because [jsdom](https://github.com/tmpvar/jsdom) doesn't run on Node 7, 
which is what the official J2V8 uses at the time of this writing.
We need jsdom to be able to run browser applications, such as React.

## Build

See `BUILDING.md` for details - here is a quick summary:

    source j2v8-cli.sh
    nodejs git clone
    nodejs diff apply

    # Disable tests, several of them fail :-/
    build -t macos -a x64 -ne --j2v8test="-Dmaven.test.skip=true"
    mvn install

After this, you should be able to use J2V8 in your Subsecond TDD Java project.