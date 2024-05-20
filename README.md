Практическое задание
Описание: Развертывание Minikube. Работа с манифестами.
Результатом работы должен быть составлен отчет о выполненной работе в
формате .pdf или ссылка на публичный репозиторий Gitlab.
Описание задания:
1. Произведите развертывание системы minikube на рабочем компьютере или
виртуальной машине.
2. Cоздайте файл pod.yaml и скопируйте в него следующий манифест:
apiVersion: v1
kind: Pod
metadata:
name: my-nginx
spec:
containers:
name: nginx-container
image: nginx:1.10
• попробуйте создать из этого манифеста pod с помощью команды
kubectl create -f pod.yaml
• kubectl не может применить yaml-файл, в чём ошибка?
3. запустите pod redis в кластере с помощью команды: kubectl run redis --
image=redis:5.0 -n default
a. проверьте, что redis запустился и находится в статусе Running, с
помощью команды: kubectl get pods -n default
b. удостоверьтесь, что версия docker image — redis:5.0, с помощью
команды: kubectl get pod redis -n default -o jsonpath=”{..image}”
c. отредактируйте pod redis с помощью команды kubectl edit pod redis -n
default так, чтобы версия docker image стала redis:6.0
Примечание: вы можете изменять текстовый редактор, используемый
командой kubectl edit по умолчанию, с помощью переменной
окружения KUBE_EDITOR — например, export KUBE_EDITOR=nano
или export KUBE_EDITOR=vim.
d. сохраните изменения и проверьте логи контейнера с помощью
команды: kubectl logs redis -n default
