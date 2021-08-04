FROM mcr.microsoft.com/dotnet/sdk:5.0.302 AS build-env
WORKDIR /app

# Copiar csproj e restaurar dependencias
COPY *.csproj ./
RUN dotnet restore

# Build da aplicacao
COPY . ./
RUN dotnet publish -c Release -o out

# Build da imagem
FROM mcr.microsoft.com/dotnet/aspnet:5.0.8
WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "WorkerEventHubQuestao.dll"]