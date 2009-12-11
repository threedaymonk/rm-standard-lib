task :default => 'index.html'
task :package => ['index.html', 'presentation.tar.gz']

file 'index.html' => FileList['{bin,src}/*'] do |t|
  Dir.chdir(File.dirname(__FILE__)) do
    rm_f "index.html"
    sh "bin/txt2s5 src/index.txt src/s5.rhtml > index.html"
  end
end

file 'presentation.tar.gz' => FileList['**/*'] - ['presentation.tar.gz'] do |t|
  rm_f t.name
  sh "tar -zcvf presentation.tar.gz --exclude #{t.name} --exclude .svn --exclude .DS_Store ../presentation"
end
