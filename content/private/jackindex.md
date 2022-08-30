<!DOCTYPE html>
<html lang="en">
{{ partial "head.html" . }}

<body>
{{partial "search.html" .}}
<div id="index" class="singlePage">
    {{partial "header.html" .}}
    <img id="banner" src="https://thdngan.github.io/quartz/banner.svg" />
    <div class="bio">
	    <article>
            <p>Hello, I'm Ngân Trịnh.</p>
            <p class="delay t-2"> You can call me Ryan!
            <div class="delay stagger">{{partial "textprocessing.html" . }}</div>
        </article>
        <div class="writing-sidebar">
            <div class="delay t-3">
	            <aside class="mainTOC">
    <details {{ if $.Site.Data.config.openToc }}open {{ end }}>
        <summary>Table of Contents</summary>
        {{ .TableOfContents }}
    </details>
</aside>
            </div>
            <div class="delay t-5">
	            <h2>My topics</h2>
	            <p>1. <a href="https://thdngan.github.io/quartz/image-processing/image-processing">Image Processing</a></p>
	            <p>2. <a href="https://thdngan.github.io/quartz/particle-physics/subatomic-particles">Particle Physics</a></p>
	            <p>3. <a href="https://thdngan.github.io/quartz/climate/climate/">Climate</a></p>
	        </div>
	        <div class="delay t-5">
                <h2>Recent Writing</h2>
                {{$writing := where .Site.RegularPages "Section" "posts" }}
                <ul class="delay stagger">
                    {{range first 3 $writing }}
                    <li>
                        <div class="section">
                            <div class="desc">
                                <h3><a href="{{ .Permalink }}">{{- .Title -}}</a></h3>
                            </div>
                            <p class="meta">
                            {{.WordCount}} words on {{partial "date-fmt.html" .}} 
                            </p>
                            {{partial "tags.html" .}}
                        </div>
                    </li>
                    {{end}}
                </ul>
                <a href="/posts">See {{sub (len $writing) 3}} more →</a>
            </div>
    </div>
</div>
<div class="delay t-5">
<hr/>
        {{partial "footerIndex.html" . }}
</div>
</body>
</html>